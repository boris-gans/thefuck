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



## New python support + install docs
**Title:**
Lack of installation guidelines and Thefuck fails when run on Windows with python versions >3.12

**Version:**
The Fuck 3.32 using Python 3.13.4 and Generic Shell

**Shell + Version:**
-   Command Prompt (Microsoft Windows [Version 10.0.26100.4061])
-   Powershell (5.1.26100.4061)

**How to reproduce:**
Install the pypi package:
```pip install thefuck```

Try running thefuck:
```thefuck``` or ```fuck```

**Output with THEFUCK_DEBUG=true:**
```log
thefuck : Traceback (most recent call last):
At line:1 char:1
+ thefuck 2> stderr.log
+ ~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (Traceback (most recent call last)::String) [], RemoteException
    + FullyQualifiedErrorId : NativeCommandError
 
  File "<frozen runpy>", line 198, in _run_module_as_main
  File "<frozen runpy>", line 88, in _run_code
  File "C:\Users\boris\AppData\Local\Programs\Python\Python313\Scripts\thefuck.exe\__main__.py", line 4, in <module>
    from thefuck.entrypoints.main import main
  File "C:\Users\boris\AppData\Local\Programs\Python\Python313\Lib\site-packages\thefuck\entrypoints\main.py", line 8, in <module>
    from .. import logs  # noqa: E402
    ^^^^^^^^^^^^^^^^^^^
  File "C:\Users\boris\AppData\Local\Programs\Python\Python313\Lib\site-packages\thefuck\logs.py", line 8, in <module>
    from .conf import settings
  File "C:\Users\boris\AppData\Local\Programs\Python\Python313\Lib\site-packages\thefuck\conf.py", line 1, in <module>
    from imp import load_source
ModuleNotFoundError: No module named 'imp'
```

**Other:**
This issue has been reported numerous times (#1508, #1501, #1491, #1489, etc.). Although this is a very easy fix which people have already explained (notably @ierezell on issue #1489), I figured it was an oppurtunity to also improve the documentation and create an installation guide. I might be a bit dull but it took me a little while to figure this out.




## Random lack of optimization error I found, probably a pretty big fix
**Setting an alias in .zshrc increases start time by about 110ms** (issue 1504)




### Powershell infinite loop I found
**when installing latest version on github with pip and running the fuck.ps1 you get stuck in an infinite loop** (didnt have python in path bozo)

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