# Chmod (Change Mod)
---
## drwxrwxrwx. 1 root root 298 17 set 13.29 file
- d = directory
- r = read
- w = write
- x = execute

|owner (u)|group (g)|others (a)|
|---------|---------|----------|
| 7 | 7 | 7 |
|rwx|rwx|rwx|

## e.g.
```bash
$ chmod 777 file
```

## permission table
|Symbol|Number|Permission|
|:----:|:----:|----------|
|---|0|None|
|--x|1|Execute|
|-w-|2|Write|
|-wx|3|Write + Execute|
|r--|4|Read|
|r-x|5|Read + Execute|
|rw-|6|Read + Write|
|rwx|7|Read + Write + Execute|

[↩️](../Linux.html)