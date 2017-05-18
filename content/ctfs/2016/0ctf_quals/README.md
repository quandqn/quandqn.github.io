### equation 

After 48 hours "fighting", our team CLGT-MeePwn was ranked 12th. Here is my idea for solution of a 2-point cryptography task – equation.
We was given a [zip](http://dl.0ops.net/equation.zip) file contain a "mask" RSA private key photo, and an encoded flag.

![](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/0ctf_quals/screenshot-2016-03-15-at-04-50-02.png)

Instead of trying to retype the private key (or using some OCR tools), I recognize that there is a private key which was hidden in the photo. Use binwalk to extract it.

![](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/0ctf_quals/screenshot-2016-03-15-at-04-35-42.png)

Based on the format of normal RSA private key, we can recover LSBs of below exponents from the given key: 

$d_ p \equiv d \mod (p -1)$

$d_ q \equiv d \mod (q -1)$

$q_{inv} \equiv q^{-1} \mod p$

If we multiply the second equation with exponent $e$, it becomes:

$\varphi(n) = (p-1)(q-1)$

$ \iff ed_q \equiv 1 &plus; k(q -1) \mod \varphi(n)$

From above equation and assuming that $e = 65537$ (default value), we know value $k(q–1)$. We also know $q$ is prime number, so $q–1$ is an even number. Try to factorize $k(q–1)$ and note that $k < e$, we can recover $q$. Redo that step with $p$ or using the "coefficient" $q_{inv}$, we can recover $p$.

When we have $p$ and $q$, now we easily decrypt the flag.

The flag is `0ctf{Keep_ca1m_and_s01ve_the_RSA_Eeeequati0n!!!}`.

[gimmick:Disqus](@qd0an)
