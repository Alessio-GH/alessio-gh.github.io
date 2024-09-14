# Password hardening policies

### Example Configuration:

```bash
$ vi /etc/pam.d/common-password
  password requisite pam_cracklib.so dict retry=3 minlen=8 difforder=4 ucredit=1 dcredit=1 ocredit=1 lcredit=1
```

- **pam_cracklib.so**: this module offers advanced options for creating complex passwords;
- **dict**: prevents the use of dictionary words;
- **retry**: sets the maximum number of retries allowed for entering a password before authentication fails;
- **minlen**: sets the minimum password length;
- **difforder**: requires at least three of the following categories: uppercase letters, lowercase letters, special characters, and numbers;
- **ucredit**: requires at least one uppercase character;
- **dcredit**: requires at least one lowercase character;
- **ocredit**: requires at least one special character;
- **lcredit**: requires at least one numeric character.

> [!WARNING]
> The contents of this article were created with the assistance of Google Gemini AI searching for /etc/login.defs

[↩️](/Linux/hardening.html)
