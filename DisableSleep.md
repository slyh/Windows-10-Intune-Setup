# Intune Reference (Disable S1-S3)
***
### Microsoft Endpoint Manager > Devices > Configuration profiles

https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles

**Platform:** Windows 10 and later

**Profile:** Administrative Templates


##### Computer Configuration/System/Power Management/Sleep Settings

Name | State | Value
-----|-------|------
Allow standby states (S1-S3) when sleeping (on battery) | Disabled
Allow standby states (S1-S3) when sleeping (plugged in) | Disabled
Require a password when a computer wakes (on battery) | Enabled
Require a password when a computer wakes (plugged in) | Enabled
Specify the system hibernate timeout (on battery) | Enabled | 0
Specify the system hibernate timeout (plugged in) | Enabled | 0
Specify the system sleep timeout (on battery) | Enabled | 0
Specify the system sleep timeout (plugged in) | Enabled | 0

# Disable S4 Hibernation
***
Execute in elevated terminal:
```powershell
powercfg.exe /hibernate off
```

# Reference
***
How to disable and re-enable hibernation on a computer that is running Windows

https://docs.microsoft.com/en-us/troubleshoot/windows-client/deployment/disable-and-re-enable-hibernation