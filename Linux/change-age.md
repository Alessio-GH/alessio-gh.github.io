## Change user password expiring date 📅
```bash
$ chage -m 1 -M 30 -I 60 -W 53 alessio
```

| -m                    | -M                    | -W                                                       | -I                                                          | alessio  |
| --------------------- | --------------------- | -------------------------------------------------------- | ----------------------------------------------------------- | -------- |
| minimum expiring days | maximum expiring days | number of days system warn you about password expiration | numer of days account is disabled after password expiration | username |

[↩️](user-config.md)
