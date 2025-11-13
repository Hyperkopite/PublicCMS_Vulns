Create content with maliciouts name :
<img width="2216" height="290" alt="image" src="https://github.com/user-attachments/assets/63e73cad-4a6d-4f3a-8e31-4941d86cc929" />

After content generation, XSS triggered in content search module:
<img width="2066" height="984" alt="image" src="https://github.com/user-attachments/assets/534d767e-01ef-4977-922a-b2bc87ef270d" />

This vuln can be considered useful when a low-privilege user with only content edit privilege can exploit this to steal the credentials of super admin. For example,steal the CSRF token via the GET request to admin/index.html
<img width="2124" height="690" alt="image" src="https://github.com/user-attachments/assets/67a863c9-beba-4642-abbe-8b37d5439b4c" />


