---
categories: 
 - Python
layout: single
title: "(Python) Email 보내기"
---

## <b>smtplib</b>

* Python 내장 함수
* 이메일 계정에 접속 및 이메일 송신 가능



```python
import smtplib

connection = smtplib.SMTP("smtp.gmail.com")
connection.starttls()
connection.login(user = EMAIL_ADDRESS, password = PASSWORD)
connection.sendmail(
    from_addr = my_email, 
    to_addrs = 수신자 EMAIL_ADDRESS, 
    msg = "Subject:hello\n\nThis is the body of email."
)
connection.close()
```

또는

```python
with smtplib.SMTP("smtp.gmail.com") as connection:
    connection.starttls() # Transport Layer Security : 메시지 암호화를 통해 서버와의 연결방식을 안전하게 함
    connection.login(user = EMAIL_ADDRESS, password = PASSWORD)
    connection.sendmail(
        from_addr = my_email, 
        to_addrs = 수신자 EMAIL_ADDRESS, 
        msg = "Subject:hello\n\nThis is the body of email."
    )
```

