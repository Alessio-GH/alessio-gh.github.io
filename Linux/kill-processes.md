## Kill processes 💀
```bash
kill [OPTION] [PID]
```
> *pkill* to kill by process name instead of PID
### OPTIONS
- **-l**: list options numbers;
- **-1**: restart;
- **-2**: interrupt like pressing CTRL+C;
- **-9**: kill forcefully;
- **-15**: kill gracefully.

## Example
- Run *top* process;
```bash
$ top
  top - 15:21:02 up  3:12,  2 users,  load average: 0,00, 0,00, 0,00
  Tasks: 209 total,   1 running, 208 sleeping,   0 stopped,   0 zombie
  %Cpu(s):  2,3 us,  9,3 sy,  0,0 ni, 83,7 id,  0,0 wa,  4,7 hi,  0,0 si,  0,0 st
  MiB Mem :    735,4 total,     89,7 free,    524,4 used,    233,0 buff/cache
  MiB Swap:   2048,0 total,   1899,7 free,    148,3 used.    211,1 avail Mem
  
      PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
     3986 mele      20   0  225908   3968   3200 R  11,1   0,5   0:00.06 top
        1 root      20   0  174176   8048   4724 S   0,0   1,1   0:02.71 systemd
      ...
```

- press CTRL+Z to send *top* in background;
- type *ps* to view active processes;
```bash
$ ps
  PID TTY          TIME CMD
  1941 pts/0    00:00:00 bash
  2111 pts/0    00:00:00 top
  2112 pts/0    00:00:00 ps
```
- use *pkill* command;
```bash
$ pkill -9 top
  [1]-  Killed           top
```

[↩️](/process-management.md)
