### Intro

Hi all, lâu quá không viết bài gì, tí nữa thì quên mình có cái blog github.

Mình và team mới tham gia cuộc thi Code War 2017 do [Framgia VN](https://www.facebook.com/FramgiaVietnam/) tổ chức. Và mặc dù không đạt thứ hạng như mong muốn, cũng như không có được suất đi Final, nhưng thôi cũng cố viết vài dòng để sau này còn có cái nhớ lại.

Cuộc thi có 3 mảng: Code Contest (Thi lập trình thuật toán - ACM); Code Puzzle (Thi tài các kiến thức bảo mật, coding, kỹ năng Google, giải quyết vấn đề,...) và AI  Tournament (Lập trình bot, AI). Mình phụ trách mảng Code Puzzle, nên sẽ viết về mảng này.

Vì team mình cũng không đạt thứ hạng tốt cho lắm, nên những cách giải của mình có thể sẽ không hay hoặc không tối ưu, mong nhận được sự đóng góp ý kiến của các bạn. 

### Welcome to Code War 2017 (5 point)

```
Welcome to Code War 2017 !  
This is flag for this task: `CodeWar{good_luck_and_have_fun}`, a proof that you solved this task. 
Submit it to score 5 points. That's it. 
(However, in other task, you have to find :) ) 
If you got bonus-ed by report system bug, those point will be added to this task.
Good luck !
```

Bài này là bài cho điểm, chắc không cần nói gì nữa.

### Point of View (20 point)

```
Well, it depends on how you see this picture:
```
![](https://codewar.framgia.vn/static/files/evok.png)

Bài này khá quen thuộc với các bạn hay chơi CTF, BTC đã giấu flag vào cuối bức ảnh, dễ dàng nhận ra được khi mở bức ảnh này bằng HexEditor hoặc dùng `strings` trong Linux.

### Old Riddle (300 point)

```
There are 7 houses: 

- Each house has a different color. 
- The people living in the houses all have a different nationality. 
- Each person has a differnet favorite drink. 
- Each house is home to a different pet. 
- Each person prefers a different type of tabaco product. 
- Each person prefers a different type of food. 
- A different type of tree grows in front of each house. 
- Each person plays a different sport. 
- Different flowers grow in front of each house. 
- Each person drives a different type of car.

Here are the clues:

- There are two houses between the crocuses and the cats.
- The person drinking soda lives directly to the right of the gray house.
- The person smoking Chersterfields lives directly to the right of the person eating steaks.
- The horses live directly to the left of the person drinking coffee.
- The person with birch trees has cats.
- There is one house between the redwoods and the snakes.
- The person eating potatoes lives directly next to the brown house.
- There is one house between the Tennis player and the person eating spaghetties on the right
- There is one house between the Swede and the driver of the Porsche.
- The cactuses grow in front of house four.
- There are two houses between the black and pink house on the right
- The dahlias grow to the right of the person drinking icetea.
- There is one house between the Rugby player and the person eating eggs on the right
- The person playing Badminton smokes Prince.
- There is one house between the palm trees and the person smoking Cubans on the left
- The person eating cheese lives to the left of the brown house.
- The turtles live directly to the right of the person smoking Chersterfields.
- There are two houses between the black house and the house the British lives in on the right
- The eucalyptus trees do not grow in front of house four.
- There are two houses between the German and the redwoods on the left
- The Renault driver lives directly next to Lacrosse player.
- There are two houses between the VW driver and the person smoking Bluemaster on the left
- The cats live directly next to the blue house.
- There are two houses between the house of the person eating potatoes and the green house on the right
- The Rolls Royce driver lives to the right of the Volvo driver.
- The Swiss lives directly next to the Badminton player.
- The Rugby player lives directly to the left of the person smoking Dunhill.
- The person in house three drinks milk.
- There are two houses between the Baseball player and the person drinking wine on the right
- There are two houses between the tortoises and the dogs.
- There is one house between the dogs and the person drinking lemonade.
- There are two houses between the pink house and the house the Swede lives in on the left
- The British lives directly next to the orchids.
- There is one house between the house where the tulips grow and the red house.
- The person in house five does not drink wine.
- There is one house between the cats and the person eating chocolate on the right
- The VW driver lives directly to the left of the Ferrari driver.
- The Rolls Royce is not parked in front of house seven.
- There is one house between the crocuses and the cactuses.
- There is one house between the German and the Marlboro smoking person.
- There is one house between the willows and the person smoking Cubans on the right
- There are two houses between the Lacrosse player and the person drinking coffee on the left
- The Italian lives in the blue house.
- There are two houses between the lilies and the Tennis player on the left
- There is one house between the Spanish and the driver of the VW on the left.
- There are two houses between the turtles and the person eating eggs.
- The Italian lives to the left of the Badminton player.
- There is one house between the lilies and the Ferrari.
- The orchids grow to the left of the Basketball player.
- The nut trees grow directly next to the person drinking wine. 

Where does everybody live?. Can you solve this riddle ? 

Compute flag as: 
```
`CodeWar{`'lemonade'[i0] + 'marlboro'[i1] + 'chersterfields'[i2] + 'tulips'[i3] + 'horses'[i4] + 'greek'[i5] + 'basketball'[i6] + 'cats'[i7] + 'hyacinth'[i8] + 'cheese'[i9] + 'cactuses'[i10] + 'orchids'[i11]`}`
```

`i0..i11` ```is number of the hourse that have that object
```

Bài này là một bài giải đố thuần tuý, không khó cho lắm, cái khó duy nhất theo mình là tiếng Anh, dễ bị nhầm phương hướng và chỉ dẫn. 

Nếu bạn muốn giải quyết bài này bằng code, thì có thể tham khảo bài [này](https://artificialcognition.github.io/who-owns-the-zebra), thay thế bằng những tham số đề cho.

Cách giải của mình thì hơi "tà đạo" một tí. Mình không cần dùng hết các dữ kiện đề cho, cũng không giải hết tất cả các nhà và đồ vật/con người từng nhà. Mình chỉ quan tâm flag, và đây là cách giải của mình: 

Dễ dàng nhận thấy, các nhà được đánh số từ 1 tới 7, vậy thì `i0..i11` cũng chỉ nằm trong tập [1..7]. Giải một số (khoảng 2, 3 cái)dữ kiện tiêu biểu, ta sẽ có được một vài case chắc chắn như `cactuses` ở nhà 4, `cats` ở nhà 3,...

Hơn nữa trong flag có những "dữ kiện" như : `'greek'[i5]`. Vậy chắc chắn `i5` nằm trong tập [1..4]; hay `'tulips'[i3]` và `'orchids'[i11]` thì chắc chắn `i3` khác `i11`,...

Kết hợp những điều kiện đó lại, ta dễ dàng "đoán" được flag:

```python 
i0 = [1,2,4,5,6,7]
i1 = [1,2,3,4,5,6,7]
i2 = [1,2,3,4,5,6,7]
i3 = [1,2,3,4,5]
i4 = [1,2,4,5]
i5 = [1,2,3,4]
i6 = [1,2,3,4,5,6,7]
i7 = 3
i8 != i3
i9 = [1,2,3,4,5]
i10 = 4
i11 = [1,2,3,5,6]
#flag = "CodeWar{" + 'lemonade'[i0] + 'marlboro'[i1] + 'chersterfields'[i2] + 'tulips'[i3] + 'horses'[i4] + 'greek'[i5] + 'basketball'[i6] + 'cats'[i7] + 'hyacinth'[i8] + 'cheese'[i9] + 'cactuses'[i10] + 'orchids'[i11] + "}"```
```

```
CodeWar{
e m n a d e
a r l b o r o
h e r s t e r
u l i p s
o r e s
r e e k
a s k e t b a
s
y a c i n t h 
h e e s e
u
r c h d s
}
```
Mình thì khá là ổn ở những trò xếp chữ xếp hình như thế này, nên không khó để thấy flag: `CodeWar{notsoeasyhuh}`

### Messed Up Poem (150 point)

```
                        Unknow Title

                                                      - by Unknow Author -

eoms tnihgs aer ettreb ltfe unisda
esmo ngefsiel meoc a tlleit oto teal
i iwll ellt ouy ohw ot tge eht falg
ouy elfw wyaa whne i dnpeeo ym ahnd
adn i lliw veern eb ebla ot cahct ouy aanig

ni sthi kbacl adn weiht dlwor ouy vgea em culroo
btu i cdulo tno velo yuo hwen i ovdel rntehao
uyo hsulod atke eth oglwlfoin nlei
ohw anc oyu eilsm dan tllsi ookl os ads
nhwe oyu tlso ieomnhgst oyu evenr dha

osem orwsd rae tetber tefl usnenpko
dan tup esceunrord newbtee hetos rodws
seom oelvs era ntaem ot eb kferanso
fi tafe oudlw vaeh uor pasth sscor edyaosm
ew lliw ieslm ot a rntergas adn og no uro wya

ni stih ilef ew era ont meatn fro heac rehot
ti cdluo ahpepn ni teh tnxe fi yuo eebilve ni rtoaneh
dan tvernco lal fo emht ot repup seac
waht ahs eomc ot eb i wlil vrnee gteerr
eht srmemoie ew aehv adem i lalhs ernve orgfte 
```

```Submit flag as: 
```
`CodeWar{` what you found here`}`

Nhìn sơ thì thấy điều đặc biệt như thế này: mỗi từ trong mỗi dòng đều bị scrambled đi, ví dụ như dòng đầu có thể được dịch là: `some things are better left unsaid`. Đến đây có hai cách làm: một, code scramble lại từng từ để ra đoạn thơ ban đầu; hai, copy đoạn vừa dịch được ở trên đi google coi thử nó ra cái gì, (hack não BTC tí, chả lẽ có ông nào ngồi làm ra bài thơ tiếng Anh thế này sao =]]). Mình thì lười, nên mình chọn cách thứ 2. 

Đúng thật là nó ra một bài thơ, tuy nhiên bài thơ "gốc" của BTC cho thì dài hơn vài câu so với bài mình tìm được. Kệ, có vài câu, dịch bằng mắt cũng được.

Những dòng thừa ra là những dòng này:

```
i will tell you how to get the flag
you should take the following line
and put underscore between those words
and convert all off them to upper case
```

Ok well play, flag kia rồi, lấy dòng tiếp theo của dòng `you should take the following line`, uppercase lên, thêm `_` vào giữa, thêm `CodeWar{` vào đầu và `}` vào cuối rồi submit thôi.

### 2D is Hard (200 point)

```
At a galaxy far far away, I hear that they only have flattened things. Even with rubick. You can ? Can you solve ?
```

![](https://codewar.framgia.vn/static/files/rubik.png)

Cá nhân mình nghĩ đây là một trong những bài ức chế nhất cuộc thi. 

Ý tưởng ban đầu nảy ra trong đầu mình là solved cái megaminx này, sau đó thì flag sẽ hiện ra, chắc nằm trên mặt nào đó. Sau khi thảo luận với team khoảng 20 phút, một đồng đội team mình đã quăng cho mình cái hình này và bảo: "em solve rồi anh, giờ anh làm gì làm đi =))"

![](https://quandqn.github.io/images/codewar/solved.png)

Nhìn mãi mà chả ra gì, mình quyết định chơi trò cắt dán thủ công lớp một:

![](https://quandqn.github.io/images/codewar/part1.jpg)

Và thành quả là:

![](https://quandqn.github.io/images/codewar/not.jpg)

![](https://quandqn.github.io/images/codewar/beginner.jpg)

![](https://quandqn.github.io/images/codewar/for.jpg)

Cầm xoay xoay cái khối "megaminx" đó suốt 3-4 tiếng đồng hồ, ăn hết 2 ổ bánh mì, nghe đồng đội blame điếc tai và cười vào mặt, cuối cùng mình cũng đã được thông não. `CodeWar{NOTFORBEGINNER}`, đúng là not for beginner thật.


### Let Take A Break (150 point)
```
The flag has the format of `CodeWar{AAAAAA_BBBBBBBB_CCCCC}`, where:

	`AAAAAA` is the anagram of the name of a street in Hanoi. AAAAAA contains only letters.

	`BBBBBBBB` can be found [here](https://pastebin.com/x87HJjsm) using the regular expression `(3[@](.{8})[å][~])` where:

		_`@` is the cracked md5 hash `578F7ADED41B684CB09D33CA23A57AB1`,
  
		_`å` is the cracked whirlpool hash `0bb51f486a79de40bc1cb61b4dfb4c5af4a4f4f82c30cfeb465677468a05416f8a1a9a2e8a90534542f4d1fea26e1790bde241762f7d3c3e046e70c9ba330cb8`,

		- `~` is the cracked SHA1 hash `bbbd558a572a105c718e04894e9ffa8756ef8402`.
   
		`@`, _`å` and `~` are animals.

	+ `CCCCC` is the screenname of a Twitter user with ID `380710??`.

The SHA256 hash of the whole string `AAAAAA_BBBBBBBB_CCCCC` (all letters are in uppercase) is: `753053aeae0d1a3fe33bd2cb31a901069873b8c37127b0d3757dd3a90313b526`.
```
Bài này lại là một bài khá quen thuộc với các bạn chơi CTF. Nhìn vào thì phần `BBBBBBBB` có thể được giải quyết rất nhanh gọn, ta làm trước. Các hash md5, sha1 và whirpool đó đều có thể được "decrypt" bằng các tool online (thực ra là tra trong db thôi, không decrypt được hàm băm đâu). Đưa các giá trị `@`, `å` và `~` vào vị trí tương ứng trong regex, paste regex lên [đây](http://regexr.com/), paste đoạn văn bản trong pastebin đề cho vào luôn, dễ dàng thấy được chỉ có một đoạn match là `WHATEVER`. 

Phần `CCCCC` thì cũng dễ, range có 100 user thôi, tìm tool online nào đó có thể show được username từ Twitter ID. Không khó khăn lắm khi tìm được kết quả thoả mãn là `UWANT`.

Còn lại phần `AAAAAA`, vì chỉ có 6 kí tự, nên cách dễ nhất là bruteforce luôn. Mình thì tìm vài cái tên đường phổ biến ở Hà Nội, cho vào cái dict, chạy vài permutations là xong. Các bạn có thể tham khảo code ở [đây](https://gist.github.com/quandqn/8637460bc9752484d516f994dffa50d8).

![](https://quandqn.github.io/images/codewar/Screen Shot 2017-04-20 at 2.12.35 AM.png)

### Shall We Play A Game (250 point)

```
Connect and play this game with us:_

Command: `nc bullandcow-challenge.framgia.vn 2015`
```

Bài này là một bài lập trình chơi game kinh điển, game được chơi là game [Bulls and Cows](https://en.wikipedia.org/wiki/Bulls_and_Cows). Đọc luật và chơi thử vài game là bạn có thể giải quyết bài này. Trên google cũng có một số code mẫu, các bạn lấy về rồi fix code lại là được :D 

### Coding is Art (50 point)

```
I promise, this task is super easy ;)_

[code.rb](https://codewar.framgia.vn/static/files/code.rb)
```

Nhìn qua thì code đơn giản, không có gì phức tạp, chỉ là in ra một loạt ký tự `xyztuv`. Có một dòng comment `#x ,y/,z),t|,u_,v(`, có lẽ là ta cần replace từng ký tự `xyztuv` với ký tự tương ứng trong comment này. 

Replace và in ra trong cùng một biến, ta có được hình như thế này:

![](https://quandqn.github.io/images/codewar/rbrbrb.png)

Tinh ý thì có thể nhận ra đây là ASCII Art. Chỉnh sửa độ dài độ rộng của các ký tự được in ra, ta có được flag.

### His Best Friend (200 point)

&nbsp;&nbsp;&nbsp;&nbsp;_My friend show me his "best friend", and his "best friend" want to say something wise_

&nbsp;&nbsp;&nbsp;&nbsp;_[wise_words](https://codewar.framgia.vn/static/files/wise_words)_

&nbsp;&nbsp;&nbsp;&nbsp;_Can you understand it ?_

&nbsp;&nbsp;&nbsp;&nbsp;_Submit flag as: `CodeWar{` enter what you found here, all lower case`}`_

Một loạt dãy số theo hàng dọc, mỗi dãy 13 số. Chắc là mã gì đây.

Sau khoảng nửa tiếng google thì team nhận ra đây là [ISBN Code](https://en.wikipedia.org/wiki/International_Standard_Book_Number). 

Một bạn trong team mình viết một script search theo ISBN code và ghi tên tất cả các tên sách ra cho mình. Sau một hồi ngẫm nghĩ nhìn tới ngó lui thì nhận ra flag có thể được cấu thành từ ký tự đầu tiên (được in hoa) của mỗi tên sách. Rất may là mình đúng.

![](https://quandqn.github.io/images/codewar/Screen Shot 2017-04-20 at 2.30.33 AM.png)

### Wall of Text (175 point)

&nbsp;&nbsp;&nbsp;&nbsp;_There is a hidden message ? (somebody told that :v)_

&nbsp;&nbsp;&nbsp;&nbsp;![](https://codewar.framgia.vn/static/files/wall.png)

Bài này là một bài steganography đội lốt crypto rất magic, rất vi diệu, rất ba chấm. Tận lúc mình làm ra mình còn không hiểu tại sao lúc đó mình có thể nghĩ được như vậy.

Một bạn team mình đã "OCR tay" tất cả các ký tự trong hình ra file text, và thử đủ kiểu encode mà không ra. Mình cũng stuck ở bài này khá lâu. Chả hiểu thế nào lúc đó mình lại nhớ tới một bài trong giải PoliCTF cũng cho file ảnh thế này. Thế là vội vàng chạy đi "hack" máy Windows thằng bạn cùng phòng, mở Paint lên, đổ màu đen vào chỗ màu trắng, sau đó đổ màu đỏ vào chỗ màu đen. Magic làm sao, vi diệu làm sao, thần kỳ làm sao, flag hiện ra trước mắt mình =))))

![](https://quandqn.github.io/images/codewar/magicvl.png)

### 8 is 8 but 8 is not 8 (100 point)

```
12573783756253821289993516661571532721735159999733657183510117532
23157187107235072287370282131575321373512705532214542504338253712
17532304457731617701230154447731752375213297235584440203439171532
25137587303551977591358133218712357175123101535103178782540737251
12753783129233055506665359991771523523751256666387210303128227531
33732315351537277752753531713535137211723323555332277131575275722
31257206665189999233657189993723175194949505718553821116661121357
73152285758307335314542587370532175311817587210235072182131712735
13527194445394444284440301230725137122022394449231617754447732175
12357387362387721703178191358253127511853302118551977733218312735
75123741279706666587210706665221375573872265720133055359991735172
```

&nbsp;&nbsp;&nbsp;&nbsp;_Submit flag as: `CodeWar{` what you found here`}`_

Bài này cũng là một bài cực kỳ hack não của BTC.

Trong CTF mình hay chơi crypto, cũng hay thấy mấy dãy số kiểu này, thế là mình đem convert sang hệ 16, rồi hệ 8 các kiểu, in ra, thấy toàn thứ tào lao, xác định là tạch.

Stuck mãi đến khi bạn mình thông não cho: "dòng số 6 không có số 8, không có số 6..."

Ơ có lẽ nào đề troll, flag được "vẽ" bằng các kí tự số nào đó và được che đi bằng các kí tự khác giống như bài Wall of Text ở trên? 

Mình replace các số 8, số 6,... bằng khoảng trắng và in ra. Vẫn tạch.

Thử replace các số có trong dòng thứ 6 thì, ô kìa, cái gì đây, magic vãi.

![](https://quandqn.github.io/images/codewar/Screen Shot 2017-04-20 at 2.46.54 AM.png)

### CodeWar.js (70 point)

&nbsp;&nbsp;&nbsp;&nbsp;_Sometimes, JS doesn't mean JS at all. [WTF](https://codewar.framgia.vn/static/files/codewar.js) ? But it a hint_

&nbsp;&nbsp;&nbsp;&nbsp;_*Hint:* something inside ?_

&nbsp;&nbsp;&nbsp;&nbsp;_*Hint:* Steganography !_

Bài này có lẽ là bài gây ức chế nhất cho mình. Đuôi `.js` nhưng thực ra đây là file ảnh PNG, vậy khả năng cao là Steganography tiếp rồi. Thử tất cả các tool steganography mình (và các bạn trong team biết) đều chả cho ra kết quả gì.

Trong cái nỗi khổ đau cùng cực vì ức chế, mình quyết định quét pixel cái hình này xem thế nào. Sau khi quét và căng mắt ra nhìn đủ 290 x 231 pixel ảnh, ánh sáng cũng loé lên với mình. Alpha plane của dòng pixel đầu tiên mang các giá trị khác nhau và khác hoàn toàn so với các pixel còn lại. Mất thêm một tiếng đồng hồ để search google tool nào giấu tin dưới ảnh ở alpha plane, cuối cùng cũng thấy nó. [Steganography.js](https://www.peter-eigenschink.at/projects/steganographyjs/), khả năng cao là nó rồi. Đem về build lên, build vỡ mặt mà không nhận ra trong link có một tab test online :'( 

Upload hình lên và thế là có flag. Một lần nữa mình đã phải thốt lên: "Magic vl!".

### Tricky-Ricky Reading (200 point)

&nbsp;&nbsp;&nbsp;&nbsp;`4 LNF OXOX1BX1 64C6CX V1 G6VF4F3 VD IGN6 4W8FN161XP, L0XXW6 6GN6 XG6 411NLN3X IN8 OXW6T, NFP 6GN6 4 CN4P DCN6 4F N 1VLFX1, XUNINFXP NFP CFV46VOX88. VFLX 4 L5V6GXP OT DNLX I46G OT GNFP NFP VD5FP OT XGLXU8 IX1X IX6 ; NFP 4 CNLX1CXP 1XPFVI4F3 GIV8X X6N18 6GXT IX1X, NFP GVI 6GXT LNOX 6V BX ; B56 TXBVFP 6G48 46 XX8OXP 4 46VFLXP G6VF4F3. N6 I8W44LG IX WV68WXP 6V 1X86, N8 855NC, DV1 NF GV51 ; NFP NC6X1 4F XG6 PNT 4 XBOXOX11XP UNI4F3 5W, N8 4D D1VO N PXXW O5C8BX1, NFP PF4D4F3 XG6 411NLN3X 5246X D5CC VD 3FX88NWX18. GVI V1 IGXF 6GXT 6VVU G6X41 NCWLX8, NFP VD IGN6 N3X, 8X0, V1 6N684VF 6GXT IX1X, 4 GN9X FV 4PXN. 4 VFCT UFVI 6GN6 6GXT LNOX NFP IXF6 C4UX XG6 NXC9X8 6GN6 VCBIXP WN86 XG6 PF4IVI8, NFP 6GN6, IV1PFXP 4F XG6 XC6GX VD OT 6LND846N884P4VF, 4 WN4P FV 6FX66N4VF VD G6TFN4F3. `

&nbsp;&nbsp;&nbsp;&nbsp;_Submit Flag as: `CodeWar{` SHA1 of decoded text with no punctuation, no space, all upper case `}`_

À, đây rồi, crypto đây rồi, sở trường đây rồi. Nhìn thế này thì khả năng cao là subtitution cipher rồi.

Cơ mà đời không như là mơ, ngồi xếp mãi mà không ra :'( phải đến khi thằng em quăng cho cái tool thì mới tỉnh ngộ: 

![](https://quandqn.github.io/images/codewar/Screen Shot 2017-04-14 at 1.31.58 PM.png)

Việc còn lại bây giờ là scramble lại các từ thôi. Cũng như bài trên, có hai cách giải quyết: một, code tìm scramble có nghĩa; hai, google tìm tool online. Mình đã đi tìm được vài từ, đến khi chợt nhận ra các từ có quy luật (thanks to my big idol):

```
>>> def x(s): return s[:-3][::-1] + s[-3:]
...
>>> x("MEMErBEr")
'rEMEMBEr'
>>> x("iPsNArtrED")
'trANsPirED'
>>> x("gNEssAPErs")
'PAssENgErs'
>>>
```

Tới đây rồi thì YOLO thôi! 

### KubEye Challenge (300 point)

&nbsp;&nbsp;&nbsp;&nbsp;_Restore it if you can ?_ 

&nbsp;&nbsp;&nbsp;&nbsp;_Challenge Accepted ?_

&nbsp;&nbsp;&nbsp;&nbsp;_[https://kube-challenge.surge.sh/](https://kube-challenge.surge.sh/)_

&nbsp;&nbsp;&nbsp;&nbsp;_Submit flag as: `CodeWar{` what you found, upper cased and put underscore between words`}`_

Èo, BTC thích cho chơi mấy trò xếp hình nhỉ. 

Mà bài này 300 điểm hơi ảo ảo, dễ quá, vào link xoay xoay mấy phát là có flag rồi :'( 

Flag ở mặt dưới nhé, làm biếng xoay lại quá nên lấy đỡ ảnh cũ của thằng em:

![](https://quandqn.github.io/images/codewar/flaggggg.png)

### Dev's Madness (375 point)

&nbsp;&nbsp;&nbsp;&nbsp;_Hey dev, are you ready for some [madness](https://codewar.framgia.vn/static/files/gitpro.zip/) ?_

Bài này Git à, chắc lại checkout rồi cat-file này nọ chứ gì :thinking_face:

Và đúng là BTC hack được não mình, đời không như là mơ. Tuy nhiên mình cũng có thấy được vài chỗ khả nghi:

![](https://quandqn.github.io/images/codewar/111.png)

![](https://quandqn.github.io/images/codewar/112.png)

Dấu hiệu của file ảnh PNG xuất hiện quá rõ ràng, IDAT, IEND,... Thế này thì rất có thể là một file ảnh PNG bị cắt ra làm nhiều phần rồi commit lên (or something else). Cơ mà nhiều branch quá, làm sao biết được branch nào mới có hình đúng, hoặc thứ tự branch nào là đúng?

Thôi, đến nước này rồi thì chỉ có bruteforce thần công thôi. Viết một script checkout và cat hết vào một file, sau đó kiểm tra xem file nào ổn thì lấy submit. 

Và, vâng, sau mấy tiếng đồng hồ chạy nóng muốn cháy máy, rất magic, chúng ta đã có một cái ảnh. Cơ mà vẫn chưa hết ác mộng, chắc do mình sida nên cái hình nó không nguyên vẹn, mà phải đoán flag nữa cơ :'( kiểu nó thế này:

![](https://quandqn.github.io/images/codewar/Screen Shot 2017-04-20 at 3.19.15 AM.png)

Và, căng mắt ra mà nhìn nào, `CodeWar{one_branch_is_not_enough}`


### Trust Me (250 point)

&nbsp;&nbsp;&nbsp;&nbsp;_It's a virus ? Dare to run [it](https://codewar.framgia.vn/static/files/9im151_fHNMp.js) ?_

Thật ra đối với team mình, bài này có solved hay không cũng không còn quan trọng, bởi vì nó không thay đổi được gì. Team mình hơi vãi khi hiểu sai luật dẫn tới việc không được chơi AI, nên giấc mơ đi Hà Nội chơi chung kết cũng tan thành mây khói. Nhưng thôi, lỡ solved hết mấy câu kia rồi mà không solve câu này cũng thấy hơi kỳ.

Sau một hồi trace đống js kia thì cũng lòi ra được một cái link [s-e-c-r-e-t-p-a-y-l-o-a-d](https://pastebin.com/RRPNHRvv). Ồ, jsfuck đây mà. Ez rồi, quăng vào [jsfuck.com](http://jsfuck.com) thôi. Run phát xem nào, ồ, cái hộp alert xinh xinh hiện ra kìa, copy flag và submit thôi. 

Ơ ơ sai flag kìa! Troll nhau! Quả cuối rồi mà BTC ơi :'(

Và người ta nói ở hiền gặp lành là đúng, ông anh huyền thoại quăng cho mình một cái [link](https://enkhee-osiris.github.io/Decoder-JSFuck/), và một lần nữa, magic làm sao, paste jsfuck vào và flag nhảy ra. 

### Kết: 

Mình xin chân thành cám ơn đồng đội, cám ơn các anh em cùng team MeePwn đã support mình, hỗ trợ mình, cũng như đã la mình, chửi mình, cười vào mặt mình để mình có động lực solve all Code Puzzle tasks.

Teamwork is da best! 

Hết rồi các bạn ạ. Chúc các bạn đi final vui vẻ nhé!