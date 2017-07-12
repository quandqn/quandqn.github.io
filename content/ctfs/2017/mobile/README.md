# info gathering

**Tìm các thông tin cơ bản về app :**

- Loại ứng dụng : native , web , hybrid app ?
- Nền tảng
- Nhà phát hành
- Changelogs các bản cập nhật
- Yêu cầu những tính năng nào của mobile 

**Các methods của app**

**Các thông tin sâu hơn**:

- Programming languages 


- Frameworks 
- APIs
- protocols 
- Các services hay app khác có liên quan / liên kết đến
- Security features, mitigations : PIE, Canary, Obfuscate, anti-debug...
- Nơi chứa data (client, server)



# Mapping

**Xây dựng env để debug app** : các device phải được root 

**Hiểu cách thức app hoạt động ** : Khi chạy yêu cầu những gì, các funcs hoạt động ra sao, dữ liệu được lưu trữ hoặc gửi đi ntn...

**Threat modeling ** : Nhờ việc hiểu cách thức app hoạt động -> Tìm được threats 

# Attack

**Client attacks** : 

- Decompile, Testing manual/fuzzing 


- Data chứa ở nơi không an toàn, có thể leak data ,... (SQLi, XMLi)
- Nếu mà là app hybird thì có thể bị XSS. 
- Runtime attacks 
- Memory corruption 

**Network attacks**:

- Sniffer , capture network traffic 
- Kiểm tra SSL/TLS 
- Authentication 
- Authorization 
- Session management 
- Mã hóa 
- Tampering 
- Crypto và protocols 

**Server attacks** : 

- TCP attacks
- HTTP attacks
- XML/ XPath injections 
- Authorization 

# References

https://www.owasp.org/index.php/IOS_Application_Security_Testing_Cheat_Sheet

https://www.owasp.org/index.php/Android_Testing_Cheat_Sheet

https://www.gitbook.com/book/b-mueller/the-owasp-mobile-security-testing-guide

https://techbeacon.com/how-hack-app-8-best-practices-pen-testing-mobile-apps







