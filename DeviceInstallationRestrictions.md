# Recommended Driver Class Whitelist
***
**Biometric Device**

Class = Biometric

ClassGuid = {53D29EF7-377C-4D14-864B-EB3A85769359}

(Windows Server 2003 and later versions of Windows) This class includes all biometric-based personal identification devices.

**System Devices**

Class = System

ClassGuid = {4d36e97d-e325-11ce-bfc1-08002be10318}

This class includes HALs, system buses, system bridges, the system ACPI driver, and the system volume manager driver.

# Intune Reference
***
### Microsoft Endpoint Manager > Devices > Configuration profiles

https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles

**Platform:** Windows 10 and later

**Profile:** Administrative Templates


##### Computer Configuration/System/Device Installation
```
Setting: Prevent device metadata retrieval from the Internet
State: Enabled
```

##### Computer Configuration/System/Device Installation/Device Installation Restrictions
```
Setting: Allow installation of devices using drivers that match these device setup classes
State: Enabled
Allow installation of devices using drivers for these device classes:
{53D29EF7-377C-4D14-864B-EB3A85769359}
{4D36E97D-E325-11CE-BFC1-08002BE10318}
```

##### Computer Configuration/System/Device Installation/Device Installation Restrictions
```
Setting: Prevent installation of devices not described by other policy settings
State: Enabled
```

# Reference
***
Class and ClassGuid entries for INF Version Section

https://docs.microsoft.com/en-us/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors