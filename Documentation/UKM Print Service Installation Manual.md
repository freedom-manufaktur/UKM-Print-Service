UKM Print Service - Installation Manual
---
Version: `1.0.0` - `2025-08-15` \
Author: [martin@freedom-manufaktur.com](mailto:martin@freedom-manufaktur.com) \
Link: [Documentation on GitHub](https://github.com/freedom-manufaktur/UKM-Print-Service/tree/main/Documentation/UKM%20Print%20Service%20Installation%20Manual.md)

Table of contents
---
<!--TOC-->
- [1. Installation](#1-installation)
  - [First time Installation](#first-time-installation)
  - [Upgrade an existing Installation](#upgrade-an-existing-installation)
  - [Unattended (silent) Installation / Upgrade](#unattended-silent-installation--upgrade)
- [Service Configuration](#service-configuration)
- [Monitoring / Debugging](#monitoring--debugging)
- [Knowledge Center Admin - Configure Service URL](#knowledge-center-admin---configure-service-url)
- [Use the service](#use-the-service)
- [What's new?](#whats-new)
  - [\[1.0.0\] - 2025-08-15](#100---2025-08-15)
- [Need support?](#need-support)
<!--/TOC-->

# 1. Installation
## First time Installation
1.  Download Installation from [UKM Print Service Download](https://freedommanufaktur.sharepoint.com/:f:/g/EhMX6-rpTWxGrZTHbR4M7egBmjveMyi0xERXPiohuq8OTw?e=pJnNZ9)
2.  *(Optional, when offline*) Download and install the most recent [.NET 9.0 Runtimes](https://dotnet.microsoft.com/en-us/download/dotnet/9.0)
    1. ASP.NET Core Runtime x64 Installer
    2. .NET Runtime x64 Installer
3.	Install `UKM Print Service Setup 1.0.0.exe`
    > Note: This will automatically install .NET 9.0 if necessary
4.  (Optional, verify running) Open a browser and navigate to \
    http://localhost:8048 \
    You should be greeted with the message\
    `Welcome to the UKM Print Service`

## Upgrade an existing Installation
1.	(Optional, when Offline) Download and install the most recent [.NET 9.0 Runtimes](https://dotnet.microsoft.com/en-us/download/dotnet/9.0)
    1.  ASP.NET Core Runtime x64 Installer
    2.	.NET Runtime x64 Installer
2.	Install `UKM Print Service Setup vNext.exe` \
    This will upgrade your existing installation.

## Unattended (silent) Installation / Upgrade
The Installer supports a [variety](https://stackoverflow.com/a/44347702/394076) of installation options. We will focus on the most important, which will be used by the UKM installer itself, to automatically provide you with an installation.

> Note:
> - When the *UKM Print Service* is already installed, it will be updated.
> - When a newer version of the *UKM Print Service* is already installed, the request will be ignored.
> - Use the PowerShell version (`PS>`) to wait for the installation to finish.

**MSI Install / Update**
```
msiexec /i "UKM Print Service Setup 1.0.0.msi" /quiet /norestart
msiexec /i "UKM Print Service Setup 1.0.0.msi" /quiet /norestart InstallFolder=C:\UKM\PrintService

PS> Start-Process C:\Windows\System32\msiexec.exe -ArgumentList '/i "UKM Print Service Setup 1.0.0.msi" /quiet /norestart' -wait
```
**MSI Uninstall**
```
msiexec /x "UKM Print Service Setup 1.0.0.exe" /quiet /norestart

PS> Start-Process C:\Windows\System32\msiexec.exe -ArgumentList '/x "UKM Print Service Setup 1.0.0.msi" /quiet /norestart' -wait
```
> Note: Instead of `/quiet` you may use `/passive` to see the progress.

---

**EXE Install / Update**
```
"UKM Print Service Setup 1.0.0.exe" -silent -norestart

PS> Start-Process 'UKM Print Service Setup 1.0.0.exe' -ArgumentList '-silent -norestart' -wait
```
**EXE Uninstall**
```
"UKM Print Service Setup 1.0.0.exe" -uninstall -silent -norestart

PS> Start-Process 'UKM Print Service Setup 1.0.0.exe' -ArgumentList '-uninstall -silent -norestart' -wait
```
> Note: Instead of `-silent` you may use `-passive` to see the progress.

# Service Configuration
> By default, the service should run out of the box, without any need for configuration.

If port `8048` (default) is already in use or you want to set any other option, then navigate to the directory \
`%ProgramData%\freedom manufaktur\UKM Print Service` \
This directory contains the configuration for the app `appsettings.json` as well as some other app files.
Editing `appsettings.json` will show something like
```
{
  "$Note": "Please refer to https://github.com/freedom-manufaktur/UKM-Print-Service for how and where to edit this file.",
  "$Help.Urls": "Enter the URLs you want the App to be available at. For example https://localhost:8049;http://localhost:8048",
  "Urls": "http://localhost:8148",
  "$Help.UseHttpsRedirection": "Should all requests to HTTP URLs be redirected to HTTPS (recommended only when publicly accessible, requires HTTPS URL).",
  "UseHttpsRedirection": false,
  "Api": {
    "$Help.EnableDetailedErrorMessages": "Enable to include the full stack trace when an error occurs while calling the API.",
    "EnableDetailedErrorMessages": true
  }
}
```
As seen in the example, the URL has been re-configured to use http://localhost:8148 as address and detailed error messages have been enabled.
> Note: After changing `appsettings.json` you must restart the `UKM Print Service` Service.

# Monitoring / Debugging

The installation creates a new Windows Service that should be running for the service to be available

![Windows Service](Images/Windows%20Service.png)

The installation also creates a new Windows Event Log source `UKM Print Service`. Please start the *Event Viewer* or any other Event Log monitoring tool to view the application logs.

![Event Log](Images/Windows%20Service%20Event%20Log.png)

# Knowledge Center Admin - Configure Service URL
By default the service should be running under the URL `http://localhost:8048`.
You can configure this URL (or another one) in the Knowledge Center Admin interface.
Enter the full URL



 TODO hier / api/print-to-pdf




 
![alt text](<Images/Knowledge Base Admin - Print Service URL.png>)

# Use the service
TODO
![alt text](<Images/Knowledge Base - Print Active Document.png>)

# What's new?
This section lists **important** changes to the documentation.
Please read this list when upgrading an existing installation.
> The full app changelog can be found in the [UKM Print Service Download](https://freedommanufaktur.sharepoint.com/:f:/g/EhMX6-rpTWxGrZTHbR4M7egBmjveMyi0xERXPiohuq8OTw?e=pJnNZ9)

## [1.0.0] - 2025-08-15
- Initial release.

# Need support?
If you have any questions regarding the installation or configuration of the *UKM Print Service*, contact us at
- All questions around the *UKM Print Service* \
  [support@freedom-manufaktur.com](mailto:support@freedom-manufaktur.com) (freedom manufaktur)
- All questions regarding the *USU Knowledge Manager* itself \
  [support@usu.com](mailto:support@usu.com) (USU)
