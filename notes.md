source: /opt/homebrew/Cellar/thefuck/3.32/libexec/bin
- calls thefuck.entrypoints.main
``` bash
import re
import sys
from thefuck.entrypoints.main import main
if __name__ == '__main__':
    sys.argv[0] = re.sub(r'(-script\.pyw|\.exe)?$', '', sys.argv[0])
    sys.exit(main())
```

#### entrypoints

1. Inits the colorama object; all it does is it gives the stdout and stderr access to colorama functions (color and bs) `thefuck.entrypoints.main line 4` --> `thefuck.system.unix/win32.py`

2. Inits parser object, customized argparse ArgumentParser object `thefuck.entrypoints.main`

    a. Defines custom flags (including conflicting); so things like --yeah/--y/--help etc. `thefuck.argument_parser.py`

3. Reads user input and decodes flags 

    a. **Understand the documentation on how they read arguements** `thefuck.argument_parser.py` @ `_prepare_arguments`

4. Runs through a series of input checks: `thefuck.entrypoints.main`

    a. Help: where is this attribute defined; **check argparse docs**

    b. Version: ...

    c. Alias + command / TF_HISTORY: a point is made abt checking for an alias before checking TF_HISTORY. What is either, what's the significance?

        -   Listed as issue 921, could be a good solve


#### output_readers


#### alias

The alias is what defines and assigns values to TF_HISTORY, allowing thefuck to actually see the CLI history. For bash, this is done at: `thefuck/shells/bash.py` @ `line 16`
-   Could be where the model gets it's input from

#### next

- run locally (not brew), add custom rules

- how do the up/down arrows work for selecting similar ones? similarity search?

### Issues
**Issue in conf.py; imp is no longer supported after python version 3.12**
-   Command Prompt:
-   PowerShell:
-   Bash:

**lack of clear installation guidelines for windows systems (command prompt and powershell)**
-   Command prompt: done
-   PowerShell:
-   Bash: (neccecesary??)

**



