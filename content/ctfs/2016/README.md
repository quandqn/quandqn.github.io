### Intro

It is very proud of me for first time playing for CLGT – the best CTF team of Vietnam. And luckily, I have solved some interesting challenge (enough for me to smile when it ends.) 

Final scoreboard:

![final](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/hitcon_quals/screenshot-2016-10-10-at-09-00-11.png)

### Hackpad (Crypto 150pts)

![hackpad](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/hitcon_quals/screenshot-2016-10-10-at-09-21-52.png)

[Download file here.](http://www.mediafire.com/file/wmuf4m3aajidzdz/hackpad.pcap.xz_968494cea2c29140ee5e63e37c19cff2254f0229)

After extracting, open the given file with Wireshark. We can see there are so many HTTP requests. Three first streams are GET requests which contains the encrypted secret (flag), others are POST requests to check whether the msg can be decrypted or not. If can, it will return a 200 status code and a md5 hash of the decrypted message; otherwise a 500 status code.

![1](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/hitcon_quals/screenshot-2016-10-10-at-11-02-56.png)

Digging in the POST requests, we can see that the client try to make a [Padding Oracle Attack](https://en.wikipedia.org/wiki/Padding_oracle_attack) by brute-force one by one byte from reversed order follow by a block of encrypted message to check for a valid  decryption. So, we obtain these correct bytes (one by one), and as this blog describe very clearly how to do a padding oracle, you can recover the original message which contains flag.

Note: for each correct byte, you can choose from calculating the next byte from previous byte, or using the data given in the pcap file as my script [here](https://gist.github.com/quandqn/0f10e0c36b2bd196f0bd2923dedc155b).

### 2. Beelzemon (PPC 150pts)

![beel](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/hitcon_quals/screenshot-2016-10-10-at-09-21-10.png)

In my very first thought, I don’t think I have chance to solve this challenge because one of my teammate is very good at this kind of problem, and he usually solves them very fast. But this time, he looks at the description and says: “Why is it so hard?” and moves to another challenge. Ok, now’s the time for me to shine (lol =]]).

After some tests and fails, and some tries to find the correct rules of the sequence, I recognize that this problem is a further case of the [Prouhet-Tarry-Escott problem](https://en.wikipedia.org/wiki/Thue%E2%80%93Morse_sequence#The_Prouhet.E2.80.93Tarry.E2.80.93Escott_problem) and it can be easily solve with a sequence called "evil number". Now it is easier, write a [script](https://gist.github.com/quandqn/9da59fd2590cea533c07aea145898b3d) to solve it.

And we have flag!

![flag](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/hitcon_quals/screenshot-2016-10-10-at-09-37-51.png)

### 3. Let’s Decrypt (Crypto 100pts)

![let](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/hitcon_quals/screenshot-2016-10-10-at-09-22-05.png)

The server allows us to view the source of the service and decrypt the ciphertext.

Source: 

```ruby
#!/usr/bin/env ruby
require 'openssl'
require 'timeout'

$stdout.sync = true
Dir.chdir(File.dirname(__FILE__))

class String
  def enhex
    self.unpack('H*')[0]
  end

  def dehex
    [self].pack('H*')
  end
end

flag = IO.read('flag')
KEY = IV = flag[/hitcon\{(.*)\}/, 1]
fail unless KEY.size == 16

def aes(s, mode)
  cipher = OpenSSL::Cipher::AES128.new(:CBC)
  cipher.send(mode)
  cipher.key = KEY
  cipher.iv = IV
  cipher.update(s) + cipher.final
end

def encrypt(s); aes(s, :encrypt) end
def decrypt(s); aes(s, :decrypt) end

m = 'The quick brown fox jumps over the lazy dog'
c = encrypt(m)
fail unless c.enhex == '4a5b8d0034e5469c071b60000ca134d9e04f07e4dcd6cf096b47ba48b357814e4a89ef1cfad33e1dd28b892ba7233285'
fail unless c.enhex.dehex == c
fail unless decrypt(c) == m

begin
  Timeout::timeout(30) do
    puts '1) Show me the source'
    puts "2) Let's decrypt"
    cmd = gets.to_i
    case cmd
    when 1
      puts IO.read(__FILE__)
    when 2
      c = gets.chomp.dehex
      m = decrypt(c)
      puts m.enhex
    else
      puts '...meow?'
    end
  end
rescue Timeout::Error
  puts 'Timeout ._./'
```

It gives us the plaintext, the ciphertext and let us know they encrypt/decrypt with AES-CBC mode with same key and IV.

Let see how CBC mode works:

![cbcencrypt](https://upload.wikimedia.org/wikipedia/commons/thumb/8/80/CBC_encryption.svg/601px-CBC_encryption.svg.png)

![cbcdecrypt](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/CBC_decryption.svg/601px-CBC_decryption.svg.png)

More clearly, if the first block has index 1, the mathematical formula for CBC encryption is ![enc1](https://wikimedia.org/api/rest_v1/media/math/render/svg/81d5dc659248a6ef5a9e7434250207da9ff3701e) with ![enc2](https://wikimedia.org/api/rest_v1/media/math/render/svg/7b8cee079a821cf0a25744655bd839d122716b73); while the mathematical formula for CBC decryption is ![dec1](https://wikimedia.org/api/rest_v1/media/math/render/svg/4d3f09299f92dca7d19e2a09c2611e797562855f) with ![dec2](https://wikimedia.org/api/rest_v1/media/math/render/svg/123befe3ec745ff58ed57c8c9ebd9ca866a3e390)

Thinking about it… what would happen if we force the server to decrypt a “wrong” ciphertext which can be extracted from the correct ciphertext?

If we divide the ciphertext (_c_) to 3 blocks $c1, c2, c3$, and send $c2 + c2 + c3$ (where `+` is concatenation operation of strings) to the server to decrypt to get the plaintext ($p'$), the server will work as below:

$$\begin{eqnarray} 
p^{'}1 &= &IV \oplus D(c2) \nonumber \\
p^{'}2 &= &c_2 \oplus D(c2) \nonumber \\
\Rightarrow IV &= &p^{'}2 \oplus c2 \oplus p^{'}1)
\end{eqnarray}$$

Yeah, really nice! That's all for this challenge.

### 4. Flame (PPC 150pts)

![flame](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/hitcon_quals/screenshot-2016-10-11-at-17-43-29.png)

[Download file here.](http://www.mediafire.com/file/ob7frfyzxhhkyjz/flame_4a1f5a4d2eedfe718fee7eff429bb7e63a0c1b69)

OMG! PowerPC! I really hate this >.<

But luckily (again), I found a very very good and impressive website, [https://retdec.com][https://retdec.com], which provide a decompiler can decompile MIPS, ARM,… and especially PowerPC to C code!

After uploading the given file to the online decompilation service of retdec, waiting two minutes, see what we have:

```c++
//
// This file was generated by the Retargetable Decompiler
// Website: https://retdec.com
// Copyright (c) 2016 Retargetable Decompiler <info@retdec.com>
//

#include <stdbool.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// --------------------- Global Variables ---------------------

char * g1; // 0x1007899c

// ------------------------ Functions -------------------------

// Address range: 0x1000078c - 0x100009bf
int main(int argc, char ** argv) {
    int32_t v1; // bp-432
    v1 = &v1;
    int32_t v2;
    memcpy((char *)&v2, (char *)&g1, 140);
    puts("*************************************");
    puts("*                                   *");
    puts("*   HITCON CTF 2016 Flag Verifier   *");
    puts("*                                   *");
    puts("*************************************");
    printf("Check your flag before submission: ");
    int32_t str;
    scanf("%s", &str);
    if (strlen((char *)&str) != 35) {
        // 0x10000964
        puts("Your flag is incorrect :(");
        // branch -> 0x10000974
        // 0x10000974
        return 0;
    }
    // 0x1000084c
    srandom(0x1e61);
    int32_t v3;
    int32_t v4 = &v3; // 0x10000874_0
    int32_t v5 = 0;
    // branch -> 0x10000860
    int32_t v6;
    while (true) {
        uint32_t v7 = rand() % 0x1000; // 0x10000868
        int32_t * v8 = (int32_t *)(v4 - 384 + 4 * v5); // 0x10000880_0
        *v8 = v7;
        unsigned char v9 = *(char *)(v5 + (int32_t)&str); // 0x100008ac
        *v8 = (int32_t)v9 ^ v7;
        if (v5 > 33) {
            v6 = 0;
            // break -> 0x100008f4
            break;
        }
        v5++;
        // continue -> 0x10000860
    }
    while (true) {
        int32_t v10 = 4 * v6 + v4; // 0x10000900
        if (*(int32_t *)(v10 - 244) == *(int32_t *)(v10 - 384)) {
            // 0x10000938
            if (v6 > 33) {
                // break -> 0x10000944
                break;
            }
            v6++;
            // continue -> 0x100008f4
            continue;
        }
    }
    // 0x10000944
    puts("Good job!! now you can submit your flag :)");
    // branch -> 0x10000974
    // 0x10000974
    return 0;
}

// --------------- Statically Linked Functions ----------------

// void * memcpy(void * restrict dest, const void * restrict src, size_t n);
// int printf(const char * restrict format, ...);
// int puts(const char * s);
// int rand(void);
// int scanf(const char * restrict format, ...);
// void srandom(unsigned int seed);
// size_t strlen(const char * s);

// --------------------- Meta-Information ---------------------

// Detected compiler/packer: gcc (5.4.0)
// Detected functions: 1
// Decompiler release: v2.2.1 (2016-09-07)
// Decompilation date: 2016-10-08 12:26:09
```

Now, is it easy enough to capture the flag?

Yeah! That's all. Thanks my idol [Tin Duong](https://blog.tinduong.pw) for some good hints and advice.

