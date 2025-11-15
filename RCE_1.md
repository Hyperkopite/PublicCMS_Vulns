When analyzing the doUploadSitefile method, it was found that the file upload function directly uses the original file name provided by the user (file.getoriginalfilename ()) to construct the file path, and only checks whether the file extension is "-site.zip" through endsWith. . Although using siteComponent getSiteFilePath to construct the path, but not for full path traversal check file name. Attackers may construct malicious file names (such as those containing path traversal characters "../") to overwrite any file.
<img width="2104" height="882" alt="image" src="https://github.com/user-attachments/assets/0075d47f-a5b0-401f-879d-739cb941d331" />

the file object is instance of org.springframework.web.multipart.support.StandardMultipartHttpServletRequest.StandardMultipartFile#StandardMultipartFile, whose getOriginalFilename() will keep path info:
<img width="2540" height="550" alt="image" src="https://github.com/user-attachments/assets/fa223c58-86fe-4214-98a5-23efe815e0f4" />
<img width="1374" height="528" alt="image" src="https://github.com/user-attachments/assets/7fb1f883-c057-4a61-93e3-fb0a4c218e60" />


implementation of getSiteFilePath(), no filtration:
<img width="2086" height="344" alt="image" src="https://github.com/user-attachments/assets/3c77483c-0313-4571-bbb3-6275f9db1459" />

implementation of upload():
<img width="1672" height="352" alt="image" src="https://github.com/user-attachments/assets/c5e2da3e-5fe5-492e-96ae-7e2574b2f260" />

PoC:
<img width="2078" height="1344" alt="image" src="https://github.com/user-attachments/assets/fc1d8df3-37aa-40f7-9647-c8c1bdd47d1c" />

AOF triggered:
<img width="1166" height="346" alt="image" src="https://github.com/user-attachments/assets/afe84c2e-f513-4310-bf18-048295dedd84" />


