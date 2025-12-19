**CVE-2025-65837**
> [Suggested description]
> A XSS vulnerability in PublicCMS content search module may lead to
> arbituary JS code execution, privilege escalation, information
> disclosure and potential DOS via some critical administratice
> operation.
>
> ------------------------------------------
>
> [Vulnerability Type]
> Cross Site Scripting (XSS)
>
> ------------------------------------------
>
> [Vendor of Product]
> @sanluan on Github
>
> ------------------------------------------
>
> [Affected Product Code Base]
> PublicCMS - V5.202506.b
>
> ------------------------------------------
>
> [Affected Component]
> Content Search module
>
> ------------------------------------------
>
> [Attack Type]
> Remote
>
> ------------------------------------------
>
> [Impact Denial of Service]
> true
>
> ------------------------------------------
>
> [Impact Escalation of Privileges]
> true
>
> ------------------------------------------
>
> [Impact Information Disclosure]
> true
>
> ------------------------------------------
>
> [Attack Vectors]
> some must create or edit the name of content
>
> ------------------------------------------
>
> [Reference]
> https://github.com/Hyperkopite/PublicCMS_Vulns/blob/main/XSS_1.md
> https://github.com/sanluan/PublicCMS
>
> ------------------------------------------
>
> [Discoverer]
> ruota.cxy of Alibaba Group Eleme Security Team

Duplicate of CVE-2025-65837 which was previously assigned to you

Create content with maliciouts name :
<img width="2216" height="290" alt="image" src="https://github.com/user-attachments/assets/63e73cad-4a6d-4f3a-8e31-4941d86cc929" />

After content generation, XSS triggered in content search module:
<img width="2066" height="984" alt="image" src="https://github.com/user-attachments/assets/534d767e-01ef-4977-922a-b2bc87ef270d" />

This vuln can be considered useful when a low-privilege user with only content edit privilege can exploit this to steal the credentials of super admin. For example,steal the CSRF token via the GET request to admin/index.html
<img width="2124" height="690" alt="image" src="https://github.com/user-attachments/assets/67a863c9-beba-4642-abbe-8b37d5439b4c" />


