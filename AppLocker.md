# Recommended Rules
***
### Executable Rules
* %PROGRAMFILES%\*
* %WINDIR%\*
* %OSDRIVE%\Users\*\AppData\Local\Microsoft\OneDrive\*
* %OSDrive%\ProgramData\Microsoft\Windows Defender\Platform\*

### Windows Installer Rules
* %WINDIR%\Installer\*

### Script Rules
* %PROGRAMFILES%\*
* %WINDIR%\*

### Packaged app Rules

# CSP Reference
***
### EXE Policy
```xml
OMA-URI: ./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/8618b660-ca48-4952-90e1-eba438f23dcc/EXE/Policy
Data type: String
Value:
<RuleCollection Type="Exe" EnforcementMode="Enabled">
  <FilePathRule Id="921cc481-6e17-4653-8f75-050b80acca20" Name="(Default Rule) All files located in the Program Files folder" Description="Allows members of the Everyone group to run applications that are located in the Program Files folder." UserOrGroupSid="S-1-1-0" Action="Allow">
    <Conditions>
      <FilePathCondition Path="%PROGRAMFILES%\*"/>
    </Conditions>
  </FilePathRule>
  <FilePathRule Id="a61c8b2c-a319-4cd0-9690-d2177cad7b51" Name="(Default Rule) All files located in the Windows folder" Description="Allows members of the Everyone group to run applications that are located in the Windows folder." UserOrGroupSid="S-1-1-0" Action="Allow">
    <Conditions>
      <FilePathCondition Path="%WINDIR%\*"/>
    </Conditions>
  </FilePathRule>
</RuleCollection>
```

### MSI Policy
```xml
OMA-URI: ./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/8618b660-ca48-4952-90e1-eba438f23dcc/MSI/Policy
Data type: String
Value:
<RuleCollection Type="Msi" EnforcementMode="Enabled">
  <FilePathRule Id="5b290184-345a-4453-b184-45305f6d9a54" Name="(Default Rule) All Windows Installer files in %systemdrive%\Windows\Installer" Description="Allows members of the Everyone group to run all Windows Installer files located in %systemdrive%\Windows\Installer." UserOrGroupSid="S-1-1-0" Action="Allow">
    <Conditions>
      <FilePathCondition Path="%WINDIR%\Installer\*"/>
    </Conditions>
  </FilePathRule>
</RuleCollection>
```

### Script Policy
```xml
OMA-URI: ./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/8618b660-ca48-4952-90e1-eba438f23dcc/Script/Policy
Data type: String
Value:
<RuleCollection Type="Script" EnforcementMode="Enabled">
  <FilePathRule Id="06dce67b-934c-454f-a263-2515c8796a5d" Name="(Default Rule) All scripts located in the Program Files folder" Description="Allows members of the Everyone group to run scripts that are located in the Program Files folder." UserOrGroupSid="S-1-1-0" Action="Allow">
    <Conditions>
      <FilePathCondition Path="%PROGRAMFILES%\*"/>
    </Conditions>
  </FilePathRule>
  <FilePathRule Id="9428c672-5fc3-47f4-808a-a0011f36dd2c" Name="(Default Rule) All scripts located in the Windows folder" Description="Allows members of the Everyone group to run scripts that are located in the Windows folder." UserOrGroupSid="S-1-1-0" Action="Allow">
    <Conditions>
      <FilePathCondition Path="%WINDIR%\*"/>
    </Conditions>
  </FilePathRule>
</RuleCollection>
```

### Note
> Delete/unenrollment is not properly supported unless Grouping values are unique across enrollments. If multiple enrollments use the same Grouping value, then unenrollment will not work as expected since there are duplicate URIs that get deleted by the resource manager. To prevent this problem, the Grouping value should include some randomness. The best practice is to use a randomly generated GUID. However, there is no requirement on the exact value of the node.

# Reference
***
AppLocker CSP

https://docs.microsoft.com/en-us/windows/client-management/mdm/applocker-csp