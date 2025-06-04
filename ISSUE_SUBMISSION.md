- the output of `thefuck --version` (something like `The Fuck 3.1 using
    Python 3.5.0`);
- your shell and its version (`bash`, `zsh`, *Windows PowerShell*, etc.);
- your system (Debian 7, ArchLinux, Windows, etc.);
- how to reproduce the bug;
- the output of The Fuck with `THEFUCK_DEBUG=true` exported (typically execute
`export THEFUCK_DEBUG=true` in your shell before The Fuck);
- if the bug only appears with a specific application, the output of that
application and its version;
- anything else you think is relevant.


**Issue 1: Failed to add thefuck to windows path using the `fuck.ps1`**

### Powershell infinite loop I found
**when installing latest version on github with pip and running the fuck.ps1 you get stuck in an infinite loop**

```powershell
    adding fuck() function to current session

    alias: This command cannot find a matching alias because an alias with the name 'fuck=eval  "$(TF_ALIAS=fuck PYTHONENCODING=utf-8 thefuck "$(fc -ln -1)")"' does not exist
    At line:1 char:1
```

Title: Infinite loop when adding thefuck to system path on powershell using `fuck.ps1`
Version:
Shell + Version:
How to reproduce:
-   pip install git+https://github.com/boris-gans/thefuck.git
-   .\open-source\thefuck\scripts\fuck.ps1
Output:


Output of above (with debug set to true):
Other:



### New python support: easy fix
**Issue in conf.py; imp is no longer supported after python version 3.12** (issue )
-   Command Prompt:
-   PowerShell:
-   Bash:

### Lack of documentation for installs, especially for windows and especially given the above error
**lack of clear installation guidelines for windows systems (command prompt and powershell)** (issue )
-   Command prompt: done
-   PowerShell:
-   Bash: (neccecesary??)

### Random lack of optimization error I found, probably a pretty big fix
**Setting an alias in .zshrc increases start time by about 110ms** (issue 1504)

