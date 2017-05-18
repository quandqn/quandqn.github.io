### Twin Primes

[Download](https://twctf7qygt6ujk.azureedge.net/uploads/twin-primes.7z-39a1a147cbf55d4d944f8eacdbdf4ee7a967dd70ef0eaaa0a1cee5c58c641483)

Look at the "encrypt.py" file, we know that the flag was encrypted by RSA cryptosystem twice, first:
$$N_1 = pq$$ 

and second:
$$ N_2 = (p+2)(q+2)$$ 

By doing a simple math, we get:
$$
\left\{
\begin{array}{l}
N1 = pq,\\
N2 = (p+2) (q+2);
\end{array}
\right.
\iff
\left\{
\begin{array}{l}
N1 = pq,\\
q = \frac{N2 - N1 -4} {2};
\end{array}
\right.\\
$$

So, we can get $p$ and $q$ by solving a simple quadratic equation: "find two numbers when know their sum and product."

### ESPer

Challenge: `nc cry1.chal.ctf.westerns.tokyo 37992`

After connecting and bypassing the boring proof_of_work, the server will generate a RSA private key, and let us choose to encrypt, decrypt, see about or exit. Choose About to know what they want us to do and how it works.

```
============================= About ===============================
You are very good ESPer, so that you can change any local variable
value to 2048 bit random integer.
 
You should specify the ESP string as the line number and variables'
name to change separated by colon.
 
For example, if the source code is below and your input is "2:x",
the line 2 works the same as "x = rand(2 ** 2048); puts x". So the
output is random number.
+---+-------------------------------------------------------------------------+
| 1| x = 3 |
| 2| puts x |
+---+-------------------------------------------------------------------------+
Encryption Source code is here.
+---+-------------------------------------------------------------------------+
| 1| n, e = read_publickey(ARGV[0]) |
| 2| print "Message m: " |
| 3| STDOUT.flush |
| 4| m = STDIN.gets.to_i |
| 5| c = encrypt(m, e, n) |
| 6| puts "Encrypted: #{c}" |
| 7| STDOUT.flush |
+---+-------------------------------------------------------------------------+
 
Decryption Source code is here
+---+-------------------------------------------------------------------------+
| 1| p, q, dp, dq, qinvp = read_privkey(ARGV[0]) |
| 2| print "Encrypted Message c: " |
| 3| STDOUT.flush |
| 4| c = STDIN.gets.to_i |
| 5| m1 = decrypt(c, dp, p) |
| 6| m2 = decrypt(c, dq, q) |
| 7| m = merge(m1, m2, p, q, qinvp) |
| 8| puts "Decrypted: #{m}" |
| 9| STDOUT.flush |
+---+-------------------------------------------------------------------------+
```

As it describes, we can overwrite any variable to a random 2048 bit integer. My first thought is change e, and use Wiener attack to solve it, but it failed because they don't print $e$ out.

But luckily, there is a simple way to have $p$ and $q$. Because the decryption is based on [RSA-CRT](https://en.wikipedia.org/wiki/RSA_(cryptosystem)#Using_the_Chinese_remainder_algorithm), and we can control message $c$, so what would happen if we change $m1$ and/or $m2$ to force the server print wrong $m$? 

If we input $c$=1 and change $m2$, then $m = random + hq$,  force it to do several times, we can recover $q$ by compute $gcd(result1 -1, result2 -1)$, and do it again with $m1$ we got $p$! With $p$ and $q$ we have all things to decrypt the flag!

The server is still alive, so you can do it yourself! Good luck!

The flag is `TWCTF{I_don’t_Lik3_ESPer_problems!}`.
