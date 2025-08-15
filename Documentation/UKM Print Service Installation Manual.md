UKM Print Service - Installation Manual
---
Version: `1.0.0` - `2025-08-15` \
Author: [martin@freedom-manufaktur.com](mailto:martin@freedom-manufaktur.com) \
Link: [Documentation on GitHub](https://github.com/freedom-manufaktur/SMConnector/tree/main/Documentation/SMConnector%20Installation%20Manual.md)

Table of contents
---
<!--TOC-->
- [1. Installation](#1-installation)
  - [Unattended (silent) Installation](#unattended-silent-installation)
  - [Upgrade an existing Installation](#upgrade-an-existing-installation)
  - [Configuration](#configuration)
- [2. Configure Service in UKM TODO](#2-configure-service-in-ukm-todo)
- [3. Use the service](#3-use-the-service)
- [What's new?](#whats-new)
  - [\[1.0.0\] - 2025-08-15](#100---2025-08-15)
- [Need support?](#need-support)
<!--/TOC-->

# 1. Installation
1.  Download Installation from [SMConnector Download](https://freedommanufaktur.sharepoint.com/:f:/g/Ei5ui1vR2N5FkDdc6O7vxIwBQ3lJ7BJrXECeTJ32JEhRsA?e=8vqyJR)
1.  *(Optional, when offline*) Download and install the most recent [.NET 8.0 Runtimes](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
    1. ASP.NET Core Runtime x64 Installer
    2. .NET Runtime x64 Installer
1.	Install `SMConnector Setup 2.3.0.exe`
    > Note: This will automatically install .NET 8.0 if necessary
1.  (Optional, verify running) Open a browser and navigate to \
    http://localhost:8000 \
    You should be greeted with the message\
    `Welcome to the SMConnector Microservice`
1.	Allow inbound traffic to the service.
    > The default port used is `8000`. You may change the port number at any time.
    - Use a Reverse Proxy, like IIS [Application Request Routing](https://www.iis.net/downloads/microsoft/application-request-routing) to redirect traffic to port `8000`.
        > This is the **recommended** option, as you can perform TLS/SSL termination before hitting the service and running the service in combination with other apps.

    **OR**

    - Configure your Windows Firewall to allow inbound traffic to port `8000`
        > Note: You must bind a certificate to this port and use TLS/SSL (see *Configuration*).

1.  As a result of the previous steps you should have a publically accessible and TLS secured endpoint like **https://SMConnector.MyCompany.com**. \
    We will use this address in the next steps.

## Unattended (silent) Installation
TODO
https://stackoverflow.com/questions/44332496/comprehensive-list-of-command-line-flags-options-for-burn-bootstrapper-in-wix


## Upgrade an existing Installation

1.	(Optional, when Offline) Download and install the most recent [.NET 8.0 Runtimes](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
    1.  ASP.NET Core Runtime x64 Installer
    1.	.NET Runtime x64 Installer
1.	Install `SMConnector Setup vNext.exe` \
    This will upgrade your existing installation.

## Configuration

If port `8000` (default) is already in use or you want to set any other option, then navigate to the directory \
`%ProgramData%\freedom manufaktur\SMConnector` \
This directory contains the configuration for the app `appsettings.json` as well as some other app files.
Editing `appsettings.json` will show something like
```
{
  "$Help.Urls": "Enter the URLs you want the App to be available at. For example https://localhost:8001;http://localhost:8000",
  "Urls": "https://localhost:8443",
  "$Help.UseHttpsRedirection": "Should all requests to HTTP URLs be redirected to HTTPS (recommended, requires HTTPS URL).",
  "UseHttpsRedirection": false,
  "Api": {
    "$Help.EnableDetailedErrorMessages": "Enable to include the full stack trace when an error occurs while calling the API.",
    "EnableDetailedErrorMessages": false
  }
}
```
As seen in the example, the URL has been re-configured to use https://localhost:8443 as address and detailed error messages have been enabled. \
*After changing `appsettings.json` you must restart the `SMConnector` Service.*

**Monitoring / Debugging**

The installation creates a new Windows Service that should be running for the service to be available

![Alt text](Images/Windows%20Service.png)

The installation also creates a new Windows Event Log source `SMConnector`. Please start the *Event Viewer* or any other Event Log monitoring tool to view the application logs.

![Alt text](Images/Windows%20Service%20Event%20Log.png)

# 2. Configure Service in UKM TODO
![alt text](<Images/Knowledge Base Admin - Print Service URL.png>)

# 3. Use the service
TODO
![alt text](<Images/Knowledge Base - Print Active Document.png>)

# What's new?
This section lists **important** changes to the documentation.
Please read this list when upgrading an existing installation.
> The full app changelog can be found in the [UKM Print Service Download](https://freedommanufaktur.sharepoint.com/:f:/g/Ei5ui1vR2N5FkDdc6O7vxIwBQ3lJ7BJrXECeTJ32JEhRsA?e=8vqyJR)

## [1.0.0] - 2025-08-15
- Initial release.

# Need support?
If you have any questions regarding the installation or configuration of the *UKM Print Service*, contact us at
- All questions around the *UKM Print Service* \
  [support@freedom-manufaktur.com](mailto:support@freedom-manufaktur.com) (freedom manufaktur)
- All questions regarding the *USU Knowledge Manager* itself \
  [support@usu.com](mailto:support@usu.com) (USU)
