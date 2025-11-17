In the upload() of ckEditorController, the method handles CSRF token with wrong parameter order.
<img width="1400" height="1077" alt="image" src="https://github.com/user-attachments/assets/a717cd58-de96-4c29-9121-3ab1b92fbfbc" />

This will cause the bypass to anti-CSRF mechanism. The attacker only needs to use fixed string "web_channel" as CSRF token to initiate successful CSRF attack:
<img width="1297" height="811" alt="image" src="https://github.com/user-attachments/assets/dd0ac7f2-5a6d-4d36-9764-ca4ad756a2e5" />

DEBUG:
<img width="1738" height="991" alt="image" src="https://github.com/user-attachments/assets/7e42ee70-793b-4a70-9caa-f5b70c1f3a85" />

So in summary, the attacker can use this logical flaw to initiate a CSRF token to administrator, which cause the real token be written to upload log. A low-privilege log administrator can use this to steal global CSRF token of super administrator, then expand larger scope of CSRF attack.
