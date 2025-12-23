# Challenge: Login Admin

Target: OWASP Juice Shop

Vulnerability Type: SQL Injection (Authentication Bypass)

Description: Gained access to the administrator account without a valid password by exploiting unsanitized user input in the login field.

## Steps to Reproduce:

Navigate to the Login page (/#/login).

Identify the administrator email via "About Us" or "Product Reviews" (Found: admin@juice-sh.op).

Inject a SQL payload into the Email field to terminate the query and comment out the password check.

Payload: admin@juice-sh.op'--

Enter a dummy value in the Password field.

Result: The backend executed the query SELECT * FROM Users WHERE email = 'admin@juice-sh.op'--' AND password = '...', which effectively ignores the password condition and logs the user in as the first matching record (Admin).
    <img width="1366" height="768" alt="Screenshot_20251223_111548" src="https://github.com/user-attachments/assets/fade0f0b-ac6a-41f5-89ec-f6bbcbffa844" />
