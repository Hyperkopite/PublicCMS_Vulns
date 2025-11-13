This vulnerability exists in the chat interface of SimpleAiAdminController. It acquires the URL of the AI service configured by the site through SimpleAiConfigComponent and uses this URL to construct external HTTP requests. Since the AI service URL is configured by the administrator in the background (stored in the SysConfigData table), and the code does not perform any security checks on this URL (such as restricting the protocol to https, prohibiting internal network IP addresses, prohibiting metadata addresses, etc.), After obtaining administrator privileges (for example, logging in with the default credentials test/test), attackers can configure chat.api.URL to any address (such as cloud server metadata address, internal network service, etc.), thereby causing server request forgery (SSRF) when the chat function is triggered. Although administrator privileges are required, the PublicCMS documentation mentions default demonstration credentials, and the management interface /admin/ is directly exposed. Therefore, this vulnerability has high practical exploitation value.

SimpleAiAdminController:
<img width="2052" height="1084" alt="image" src="https://github.com/user-attachments/assets/75fcb363-c31b-4eec-9a55-1675fd7032a7" />

implementation of com.publiccms.logic.component.config.SimpleAiConfigComponent#getChatRequest()
<img width="2052" height="716" alt="image" src="https://github.com/user-attachments/assets/f3f2c1c3-8acc-4b99-b760-6205c29fd813" />
The API URL is from the user configuration.

DEMO:

1. set the maliciout URL:
<img width="2886" height="786" alt="image" src="https://github.com/user-attachments/assets/356a8a27-98a4-47f8-8390-6dad4da46ba6" />

2. When anyone using the AI in editor, SSRF triggered:
<img width="2884" height="1232" alt="image" src="https://github.com/user-attachments/assets/67e78588-5bc8-4e62-8aba-590804e42639" />

<img width="1442" height="184" alt="image" src="https://github.com/user-attachments/assets/c4b1c56b-7a5a-4900-b94e-76574eebed12" />



