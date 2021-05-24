
# one-liner-for-everything*

######  * From my perspective as a newbie dev,  I think you can automatically install and run most programs  available out there, let me know if I'm wrong!

Want to automate your script/program/whatever and make it easy for people to install it? This repo documents some tips you can use to automate your Windows installs!


# PowerShell

PowerShell is a scripting and coding language that's installed out of the box on Windows. There's command you can use to execute a .py/.bat/.ps1 (PowerShell) script easily:
```
powershell iex ((New-Object System.Net.WebClient).DownloadString('https://git.io/Jsz3F'))
```
> [This](https://git.io/Jsz3F) script you see above gets ran with this one-liner you can use to install my [toolbox](https://github.com/couleurm/couleurstoolbox/), it installs Chocolatey, then installs Git with Chocolatey,  clones my toolbox and puts it on the Desktop, no zip extractions or manual downloads needed! If your programs has dependecies just use Chocolatey.

### How to run it
Instead of opening Windows+X to select PowerShell (Admin) and pasting it in, I prefer doing this, which only requires the use of your keyboard after the one-liner being copied:

 Copy it, open Run with `Windows+R` and paste it in, then press `CTRL+SHIFT+ENTER` to run it as Admin, `LEFT(Arrowkey)+ENTER` to quickly allow the UAC prompt, and that's it.

# Batchfile

If you wanna automate the download of a file, you can use `Invoke-WebRequest` to quickly download & execute a specific file from a URL 

I've used it in my toolbox to install programs but not all program websites provide download links for the latest version, some of the time the download links to an URL that specifies the program's version inside of it, this means you'll need to manually change the URL to one that links to a newer version when it updates. If you're installing program I strongly recommend using [Chocolatey](https://chocolatey.org/) instead.

Here's what I provide in my toolbox for people to automatically download & run an installer for a specific OBS version 
```
#Downloads the file
Invoke-WebRequest "https://github.com/obsproject/obs-studio/releases/download/25.0.8/OBS-Studio-25.0.8-Full-Installer-x64.exe" -OutFile "%temp%\OBS_install.exe"
#Executes it
%temp%\OBS_install.exe
```

