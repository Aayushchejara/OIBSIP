# Task 9: SQL Injection — Advanced

**Name:** Ayush Chejara
**Track:** Cyber Security
**Company:** Oasis Infobyte

## Objective
To perform an advanced SQL Injection on a medium-security environment and understand the difference between client-side and server-side validation.

## Methodology & Execution
The target was DVWA running on localhost with the security level set to **Medium**.

Unlike the Low-security level, the application replaced the text input field with a dropdown menu to prevent arbitrary SQL commands from being typed. However, this is a **Client-Side Control**, which is inherently insecure.

**The Bypass:**
1. I used the browser's Developer Tools (Inspect Element) to modify the Document Object Model (DOM).
2. I altered the HTML `<option value="1">` tag, changing the hardcoded value to my SQL injection payload: `1 OR 1=1`.
3. Submitting this modified request bypassed the frontend restriction and successfully dumped the database records (as shown in the attached screenshot).

## Remediation
This task proves that client-side restrictions (like dropdowns, hidden fields, or JavaScript validation) can be trivially bypassed. Security must ALWAYS be enforced on the server side. 
To fix this vulnerability, developers must:
1. Implement strict server-side input validation.
2. Use **Prepared Statements (Parameterized Queries)** to ensure the backend database treats the input purely as data, never as executable code.
