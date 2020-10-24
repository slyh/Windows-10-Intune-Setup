# Intune Reference
***
### Microsoft Endpoint Manager > Devices > Configuration profiles
https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles

***

#### Disable delivery optimization

**Platform:** Windows 10 and later

**Profile:** Delivery Optimization

Setting | Value
--------|------
Download mode | Simple download mode with no peering (99)

***

#### All sorts of things

**Platform:** Windows 10 and later

**Profile:** Device restrictions
```
Evaluate all the options.
```

***

#### Windows Hello for Business

**Platform:** Windows 10 and later

**Profile:** Identity protection
```
Evaluate all the options.
```

***

#### Turn on Credential Guard 

**Platform:** Windows 10 and later

**Profile:** Endpoint protection

##### Microsoft Defender Credential Guard
Setting | Value
--------|------
Credential Guard | Enable with UEFI lock

***

#### Disable Xbox services

**Platform:** Windows 10 and later

**Profile:** Endpoint protection

##### Xbox services
Setting | Value
--------|------
Xbox Accessory Management Service | Disabled
Xbox Live Auth Manager Service | Disabled
Xbox Live Game Save Service | Disabled
Xbox Live Networking Service | Disabled