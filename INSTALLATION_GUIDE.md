# Installation Guide
i need to differentiate between normal installs and dev installs. Unfortunatley I think the only way to get it working on CMD is by doing some annoying path work, so maybe i can create an extension of the .bat script to automate this.
-   Also, have this fork also fix the import error with imp, should be quite simple

**found an error on powershell**:
pip install git+https://github.com/DL909/thefuck.git

& "C:\Users\boris\open-source\thefuck\scripts\fuck.ps1

stuck in an infinite loop:
    adding fuck() function to current session

    alias: This command cannot find a matching alias because an alias with the name 'fuck=eval  "$(TF_ALIAS=fuck PYTHONENCODING=utf-8 thefuck "$(fc -ln -1)")"' does not exist
    At line:1 char:1


## Windows

### Command Prompt (CMD)

If you've previosuly used pip to install thefuck, undo it:
`pip uninstall thefuck`


Install the maintained GitHub fork at *https://github.com/boris-gans/thefuck.git*

This fixes the import error with imp in the newer (>3.12) versions of python.
`pip install git+https://github.com/DL909/thefuck.git`

Create a new custom direcory at your *system root*, such as:
-   C:\Scripts
-   C:\Dev\bin
-   C:\Tools

`mkdir Tools`


Move the `fuck.bat` file (located at `thefuck/scipts/fuck.bat`) to this new custom directory.

(PowerShell):
`Move-Item -Path "C:\Users\boris\open-source\thefuck\scripts\fuck.bat" -Destination "C:\Tools\"`


Add the custom folder to your System Path:

    (GUI): 
        Environment Variables --> Edit the system environment variables --> Environment Variables --> User variables
        --> Select Path --> Click Edit --> Click New, and add the file path of bat file in the custom directory 
        (`C:\Tools\fuck.bat`) --> Hit OK on all windows

    (PowerShell):
        $folderToAdd = "C:\Tools\thefuck"
        $userPath = [Environment]::GetEnvironmentVariable("Path", "User")

        if (-not ($userPath.Split(';') -contains $folderToAdd)) {
            $newPath = "$userPath;$folderToAdd"
            [Environment]::SetEnvironmentVariable("Path", $newPath, "User")
            Write-Output "Added $folderToAdd to User PATH."
        } else {
            Write-Output "$folderToAdd is already in the User PATH."
        }


Restart CMD and try it out!

`sl`
`fuck`

### PowerShell + Command Prompt

If you've previosuly used pip to install thefuck, undo it:
`pip uninstall thefuck`

Install the github repository rather than the pypi package, this avoids the common import error thats a result of the `imp` package being removed after Python 3.12
`pip install git+https://github.com/nvbn/thefuck.git`

If this doesn't work there's two cases:
1.  Python and/or pip are not in your system path
2.  You did something wrong



