## Change user account default configuration ©️

```bash
$ vi /etc/login.defs
```

### - ID settings:
- UID_MIN: minimum user ID number;
- UID_MAX: maximum user ID number;
- GID_MIN: minimum group ID number;
- GID_MAX: maximum group ID number;

### - Password settings:
- PASS_MAX: maximum number of allowed password changes;
- PASS_WARN: warning period before password expiration;
- PASS_MIN_LEN: minimum password length;
- PASS_MAX_LEN: maximum password length;
- PASS_MIN_DAYS: minimum number of days between password changes;
- PASS_MAX_DAYS: maximum number of days between password changes;
- PASS_DAYS_BETWEEN_CHANGE: minimum number of days between password changes;
- PASS_WARN_AGE: warning period before password expiration;

### - Login restrictions:

- LOGIN_TIMEOUT: maximum login timeout in seconds;
- LOGIN_RETRY: maximum number of login attempts before a lockout;
- LOGIN_DELAY: delay between failed login attempts;

### - Other default settings:

- UMASK: file creation mask for new users;
- HOME_DIR: home directory for new users;
- SHELL: shell for new users;
- MAIL_DIR: mail directory for new users;
- MAIL_CHECK: frequency of mail checks.

> [!WARNING]
> The contents of this article were created with the assistance of Google Gemini AI searching for /etc/login.defs

[↩️](/Linux/user-config.html)
