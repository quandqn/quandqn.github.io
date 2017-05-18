### logarithms are hard - Misc (10 pts)
```
What is e^(1.000000001)? 
```

PlaidCTF has a series about `X is hard`, where `X` is a math operator.

So, like the past years, we should find some `bug` in operator that made the result `wrong`. And this year's `bug` is [logarithms bug](http://www.datamath.org/Story/LogarithmBug.htm).


### zipper - Misc (50 pts)

Given a zip file, try to unzip it, but failed.

Open it as hexdump, we can see that the filename is blank, and the bytes that defined the length of filename seem strange.

After using this [link](https://users.cs.jmu.edu/buchhofp/forensics/formats/pkzip.html) to know about PKzip file structure and re-checking the hexdump, quickly, we see that the filename will have a length of 8.

Then change the byte that define the filename len to "0800", and change the filename to any string with length of 8 (i choose `flag.txt`)

Extract the new zip file and capture the flag.

One-line solution:

```python
open("flag.zip", "w").write(open("zipper.zip").read().replace(")#", "\x08\x00").replace("\x00"*8+"\x55\x54", "flag.txtUT"))
```

### Down the Reversing - Hole Misc (50 pts)

```
$ file reversing-hole_c344571f488311a2553d2cbac6fa0d35.exe
reversing-hole_c344571f488311a2553d2cbac6fa0d35.exe: MS-DOS executable, MZ for MS-DOS
```

Just run it on dosbox give us flag: 

![](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2017/plaidctf/screen-shot-2017-04-24-at-2.16.31-AM.png)

### Multicast - Crypto (175 pts)

`e = 5`, so small, maybe we can solve this task by using Hastad broadcast attack.

Check out this [link](https://www.wikiwand.com/en/Coppersmith%27s_attack#/Generalizations) for more information about Hastad broadcast attack.

Solution [here](https://gist.github.com/quandqn/17ccdfde1dbfdcfe935600789121efc1):

```python
f = open('data.txt').read().strip() 

f = f.split('\n')
f = map(int, f)
ai = f[0::4]
bi = f[1::4]
ci = f[2::4]
ni = f[3::4]

def mul(ni):
	res = 1 
	for n in ni:
		res *= n
	return res 

N = mul(ni)

Ti = [[1,0,0,0,0], 
	[0,1,0,0,0],
	[0,0,1,0,0], 
	[0,0,0,1,0], 
	[0,0,0,0,1]]

P.<x> = PolynomialRing(Zmod(N))

# Find coefficient 

T = [] 
for t in Ti:
	tmp = crt(t,ni)
	T.append(tmp)

f = 0
for i in range(len(ai)):
	f += (i+1)*T[i]*( (ai[i]*x + bi[i])^5 - ci[i])

f = f.monic()
X = var('X')

# The flag is less than 512 bits
flag = f.small_roots(X=2^512, beta=0.5)

print flag
```
