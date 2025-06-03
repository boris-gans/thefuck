# Installation Guide
i need to differentiate between normal installs and dev installs. Unfortunatley I think the only way to get it working on CMD is by doing some annoying path work, so maybe i can create an extension of the .bat script to automate this.
-   Also, have this fork also fix the import error with imp, should be quite simple



## Windows

### Command Prompt (CMD)

If you've previosuly used pip to install thefuck, undo it:
`pip uninstall thefuck`


Install the maintained GitHub fork at *https://github.com/DL909/thefuck.git*

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

