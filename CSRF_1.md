In the upload() of ckEditorController, the method handles CSRF token with wrong parameter order.
<img width="1064" height="672" alt="image" src="https://github.com/user-attachments/assets/dd733085-ecc9-4bbf-abcd-c82e5525c8a2" />

The CSRF token is fixed to a constant string:
<img width="748" height="127" alt="image" src="https://github.com/user-attachments/assets/3a3f64aa-c557-49bc-8af3-f46ceeeb8354" />


This will cause the bypass to anti-CSRF mechanism. The attacker only needs to use fixed string "web_channel" as CSRF token to initiate successful CSRF attack:
<img width="2614" height="1614" alt="image" src="https://github.com/user-attachments/assets/891fc002-7531-4003-9f58-7fbf6ece2f6b" />



PoC:
<img width="512" height="111" alt="image" src="https://github.com/user-attachments/assets/7ca56347-5e9a-400f-9308-9ad362327c66" />
<img width="1140" height="563" alt="image" src="https://github.com/user-attachments/assets/e15c8d28-85b1-46cf-9952-3f124877d20d" />

So in summary, the attacker can use this logical flaw to initiate a CSRF token to administrator, which cause the real token be written to upload log. A low-privilege log administrator can use this to steal global CSRF token of super administrator, then expand larger scope of CSRF attack.


