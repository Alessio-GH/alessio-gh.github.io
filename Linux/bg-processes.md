## Background execution 🌤️
- Press CTRL+Z to put a process in background;
- type *jobs* to visualize background processes;
```bash
$ jobs
  [1]-  Fermato                 top
  [2]+  Fermato                 bc
```

- type *bg* to visualize last background process;
```bash
$ bg
  [2]+ bc &
  
  [2]+  Fermato                 bc
```

- type *fg* to bring the most recent background process to the foreground or specify the process number using *%*.
```bash
$ fg %1
```

[↩️](/process-management.html)
