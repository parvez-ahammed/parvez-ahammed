# Introduction

Well just like any tech geek I was trying to customize my command prompt and I found out that I can do it in PowerShell. So I started to search for the ways to do it and I found out that there are many ways to do it. So I decided to write this article to share my findings with you.

# What is PowerShell?

PowerShell is a task automation and configuration management framework from Microsoft, consisting of a command-line shell and associated scripting language built on the .NET Framework. PowerShell provides full access to COM and WMI, enabling administrators to perform administrative tasks on both local and remote Windows systems as well as WS-Management and CIM enabling management of remote Linux systems and network devices.

# What is Windows Terminal?

Windows Terminal is a new, modern, feature-rich, productive terminal application for command-line users. It includes many of the features most frequently requested by the Windows command-line community including support for tabs, rich text, globalization, configurability, theming & styling, and more.

You know more about it from [here](https://docs.microsoft.com/en-us/windows/terminal/).

# Customizing PowerShell

Well now you can customize your PowerShell in many ways. I will be sharing some of the problems that I found out while following the documentation.

 ## winget: the term 'winget' is not recognized as a name of a cmdlet

### Solution

1. Make sure to install winget.
- via Microsoft Store
-- Open the Windows Start menu, type store, and press Enter to open the Microsoft Store app.
--In the search bar, type winget and press Enter. In the results, click the App Installer application.
-- On the App Installer page, click Get to install the app
-- Verify the installation by invoking winget in Windows PowerShell or the Command Promp by typing 
```powershell
winget
```

- Via Github
-- Navigate to the [winget GitHub](https://github.com/microsoft/winget-cli) page.
-- Under the Releases section, click the latest available release.
-- On the Version page, scroll down to the Assets section and click the .msixbundle file to start the download
-- Run the downloaded file and click Update
-- Wait for the installation process to finish. The app may automatically install additional dependencies required for winget to work.
-- Verify the installation by running winget in PowerShell or Command Prompt

2. Make sure to add the path to the environment variables.
-- Open the Windows Start menu, type env, and press Enter to open the Environment Variables window.
-- In the System variables section,undeer User variables select Path and click Edit.
-- In the Edit environment variable window, click New and add the path to the winget installation folder. UserProfile%\AppData\Local\Microsoft\WindowsApps.
-- Click ok and again verify it

## Advance Functionality

Well aside from the basic customization you can also customize your PowerShell to a great extent. You can add aliases, functions, modules, and many more things. I will be sharing some of the things that I found out while following the documentation.

You can navigate to your Document directorys PowerShell   fodler to see  the PowerShell profile and edit it according to your needs. My profile is given below for reference.

You can edit it using text editor like notepad or notepad++ or you can use PowerShell ISE or Visual Studio Code.



```powershell

# Importing the git module 
Import-Module posh-git

# Importing the oh my posh module 
Import-Module oh-my-posh

# setting the theme of oh-my-posh module
Set-PoshPrompt M365Princess

# PSReadLine module for enhanced command line editing
Import-Module PSReadLine
Set-PSReadLineOption -EditMode Emacs
Set-PSReadLineOption -BellStyle None
Set-PSReadLineOption -PredictionSource History

# Terminal-Icons module for displaying icons in the prompt
Import-Module -Name Terminal-Icons

# Creating an alias for the 'git' command
Set-Alias g git

# Defining a function called 'art'
function art($arg1,$arg2,$arg3,$arg4,$arg5) {
    # Executing the 'php artisan' command with the provided arguments
    php artisan $arg1 $arg2 $arg3 $arg4 $arg5
}

# Creating an alias 'a' for the 'art' function
Set-Alias a art

```

## In Visual Studio Code as Windows PowerShell that is not customized

Well you can just create another folder in the Document directory named WindowsPowerShell and copy all the content of PowerShell to this directory and then you can customize it according to your needs.


# Conclusion
I am not good at writing articles so please forgive me for any mistakes. I will be updating this article as I learn more about PowerShell. I just shared what I did to customize my PowerShell. I hope you find it useful. 
Feel free to share your thoughts and suggestions in the comments section below.