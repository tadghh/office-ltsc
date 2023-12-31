# Office LTSC
A configuration file to be used with [Office Deployment Tool](https://officecdn.microsoft.com/pr/wsus/setup.exe)

New configurations can be created with [Office Customization Tool](https://config.office.com/deploymentsettings)

## Usage

The below command will start the installation with the provieded configuration.
* Assuming the below mentioned files are located in the same location
* Setup.exe refers to Office Deployment Tool
```pwsh
.\setup.exe /configure .\OfflineOfficeLTSC.xml
```
### One liner
Copy and paste this whole command into powershell.
```powershell
Invoke-WebRequest -Uri "https://officecdn.microsoft.com/pr/wsus/setup.exe" -OutFile "$env:TEMP\Office-Deployment-Tool.exe";
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/tadghh/office-ltsc/main/OfflineOfficeLTSC.xml" -OutFile "$env:TEMP\OfflineOfficeLTSC.xml";
Set-Location $env:TEMP;
.\Office-Deployment-Tool.exe /configure .\OfflineOfficeLTSC.xml;
Remove-Item ("$env:TEMP\Office-Deployment-Tool.exe"),("$env:TEMP\OfflineOfficeLTSC.xml") -Force;

```

## Info
- Version: Office LTSC Professional Plus 2021 - VL
- Language: English (United States)
- Auto Shut down running applications
- Non-Silent (Install UI will be displayed)
- Uninstalls MSI versions of
	- Visio
	- Project
	- SharePoint Designer
	- InfoPath
- Installs
  - Word
  - Excel
  - PowerPoint
## Changes
- Removed
	- Access
	- Skype for Business
	- OneNote
	- Outlook
	- Publisher
	- OneDrive Desktop
 - Behaviour
   - Disabled Automatic Updates
   - Auto Accepted EULA
   - Hidden
     - Learn more SharePoint hyperlink
     - Screen Tips
   - Disabled Telemetry
     - [Send Personal Information](https://admx.help/?Category=Office2016&Policy=office16.Office.Microsoft.Policies.Windows::L_Sendcustomerdata)
     - Online Content (Office is not allowed to connect to the Internet)
     - [User Proofing Tools Improvements](https://admx.help/?Category=Office2016&Policy=office16.Office.Microsoft.Policies.Windows::L_ImproveProofingTools)
     - [Customer Experience Improvement Program](https://admx.help/?Category=Office2016&Policy=office16.Office.Microsoft.Policies.Windows::L_EnableCustomerExperienceImprovementProgram)
     - Reliability Updates
     - Error Reporting for files the fail validation
