### Misc 100

We were given a [tcpdump capture file](http://www.mediafire.com/download/655bbeygb67s77k/tmctf100.pcap) (a Linux "cooked" capture, `the pseudo-protocol used by libpcap on Linux to capture from the “any” device and to capture on some devices where the native link layer header isn’t available or can’t be used.`)

Using Wireshark to open it. Let see:

![1](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/trendmicro_quals/screenshot-2016-07-31-at-11-35-48.png)

In `Protocol`, we can see a lot of ISAKMP (stand for `Internet Security Association & Key Management Protocol`), a protocol for establishing Security Association (SA) and cryptographic keys in an Internet environment, used in IPSec. By using this protocol, data was encrypted as we see below:

![2](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/trendmicro_quals/screenshot-2016-07-31-at-11-46-41.png)

![3](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/trendmicro_quals/screenshot-2016-07-31-at-11-51-35.png)

Following the TCP stream of Telnet session, we can see that an user tried to login. The right `username/password` is `reds/ynwa`. 

Then he showed us some good things:

![4](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/trendmicro_quals/screenshot-2016-07-31-at-12-09-16.png)

By using the command `sudo ip xfrm state`, he showed us the IPSec implementation! This is what we need to decrypt the ESP packets! Now we can use these parameters to create and add two ESP SAs. We can also use this guide to do that easily: [https://ask.wireshark.org/questions/12019/how-can-i-decrypt-ikev1-andor-esp-packets](https://ask.wireshark.org/questions/12019/how-can-i-decrypt-ikev1-andor-esp-packets)

![5](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/trendmicro_quals/screenshot-2016-07-31-at-12-09-16.png)

After successfully adding two ESP SAs, now we can decrypt the packets:

![6](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/trendmicro_quals/screenshot-2016-07-31-at-12-12-01.png)

And exporting the HTTP object to get the flag.

![7](https://raw.githubusercontent.com/quandqn/quandqn.github.io/master/images/2016/trendmicro_quals/screenshot-2016-07-31-at-12-14-57.png)

