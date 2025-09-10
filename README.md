# 🔐 Password Validator System with OTP & Logging  

This project is a **Python-based authentication system** that allows users to log in securely with multiple attempts. If they forget their password, the system helps them reset it via **OTP (One-Time Password) sent through Twilio** 📲.  

---

## ✨ Features
- ✅ **Credential Management**:  
  - Credentials are stored in a text file (`Credentials-New.txt`) in the format:  
    ```
    username,password,phone
    ```
  - The system loads and saves updates automatically.

- 🔑 **Password Validation**:  
  - Users have up to **5 attempts** to enter the correct password.  
  - Each attempt is logged for auditing 📝.

- 📲 **Forgot Password with OTP**:  
  - If the user forgets their password, the system generates a **6-digit OTP** using `random`.  
  - The OTP is sent to the registered mobile number using **Twilio API**.  
  - After OTP verification, the user can set a new password, which updates the credentials file.  

- 📂 **Logging**:  
  - All login attempts, OTP events, and errors are recorded in `password_attempts.log`.  
  - Logs include:  
    - Successful logins ✅  
    - Wrong password attempts ❌  
    - OTP sent or failed 🚀  
    - Password reset actions 🔄  

---

## ⚙️ Workflow
1. 🧑‍💻 User enters their **username**.  
   - If invalid → ❌ Access denied.  
2. 🔑 User enters password.  
   - If correct → ✅ Access granted.  
   - If wrong → Attempts left are shown.  
3. 🤔 If user chooses *Forgot Password*:  
   - OTP is generated & sent via Twilio.  
   - If OTP matches → User resets password & file updates.  
   - If OTP fails → ❌ Reset denied.  
4. 🚫 After 5 wrong attempts → Access is denied.  

---

## 📦 Dependencies
- Python `logging` (built-in) 📝  
- `random` (built-in) 🎲  
- [`twilio`](https://www.twilio.com/docs/usage/api) 📲  

Install Twilio using:

Logging Details:

INFO: User Alice logged in successfully.
WARNING: User Bob entered wrong password (Attempt 2).
ERROR: User John exceeded maximum attempts. Access denied.

🎯 Use Cases

🔐 Secure login systems

🏫 Student/Employee portals

🛡️ Authentication training projects


| 🔧 Component        | 📖 Description                                            | 📝 Example/Note         |
| ------------------- | --------------------------------------------------------- | ----------------------- |
| 👤 Username         | User enters their login name                              | `"Alice"`               |
| 🔑 Password         | Must match stored password in file                        | `"mypassword123"`       |
| 📂 Credentials File | Stores `username,password,phone`                          | `Credentials-New.txt`   |
| 🎲 OTP Generator    | Creates random 6-digit OTP                                | e.g., `823456`          |
| 📲 Twilio SMS       | Sends OTP to registered phone number                      | `"Your OTP is: 823456"` |
| 🔄 Password Reset   | Updates password in credentials file after OTP validation | New password saved ✔    |
| 📝 Logging System   | Tracks login attempts, OTP events, errors                 | `password_attempts.log` |
| 🚫 Max Attempts     | User locked out after 5 wrong attempts                    | "Access Denied!"        |



```bash
pip install twilio
