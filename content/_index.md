## About

Have you ever been running a long command and thought "I wonder how long ago that output is from"?
Well wonder no more!
With TimeStamper, you can **KNOW** exactly when a console output was from.

TimeStamper grew out of a desire.
A desire to have some indication of when a command output the output it did.

## Installation

TimeStamper is a .Net application that can be installed anywhere that .Net is supported.

### Windows with Chocolatey

Installation on Windows is just a `choco install timestamper -y` away.

The benefit of this method is that you don't require .Net to be installed in order to run TimeStamper.

### macOS, Linux, Windows

Are you on an operating system other than Windows?
Perhaps you don't want to install TimeStamper with the Chocolatey package.
In that case, you can install TimeStamper as a .Net Global Tool: `dotnet tool install timestamper.tool --global`

## Usage

Using TimeStamper is pretty straightforward.
TimeStamper itself takes a single parameter: the path to the application you want to time stamp.
It then takes the remaining arguments and passes them as arguments to the application.

There are a few ways you can make this easier with your shell should you choose to.

### PowerShell wrapper

If you're using PowerShell as your shell of choice, add the below function to you `$Profile`, then add whatever `New-Alias` commands you want to wrap.

```powershell
function timestamper {
    $app = Get-Command $MyInvocation.InvocationName -CommandType Application | Select-Object -First 1
    & TimeStamper.exe $app.Source @args
}

New-Alias git timestamper
```

### zsh wrapping

zsh (and I'm sure other shells) also allow you to set up aliases.
Add this line to your `.zshrc` file to wrap `git` output: `alias git="timestamper /usr/local/bin/git"`
