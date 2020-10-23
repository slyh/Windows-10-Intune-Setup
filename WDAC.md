# Setup
***
### 1) Create block.xml with [Microsoft recommended block rules](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/microsoft-recommended-block-rules)**

### 2) Add rules to allow windir and Program Files directories and merge with default Windows rules and recommended block rules**
```powershell
$SourcePolicies = "block.xml","C:\Windows\schemas\CodeIntegrity\ExamplePolicies\DefaultWindows_Enforced.xml";
$ResultPolicy = "result.xml";
Merge-CIPolicy -OutputFilePath $ResultPolicy -PolicyPaths $SourcePolicies
Set-CIPolicyIdInfo -FilePath $ResultPolicy -ResetPolicyID
```
or (with path rules)
```powershell
$SourcePolicies = "block.xml","C:\Windows\schemas\CodeIntegrity\ExamplePolicies\DefaultWindows_Enforced.xml";
$ResultPolicy = "result.xml";
$PathRules += New-CIPolicyRule -FilePathRule "%windir%\*";
$PathRules += New-CIPolicyRule -FilePathRule "%OSDrive%\Program Files\*";
$PathRules += New-CIPolicyRule -FilePathRule "%OSDrive%\Program Files (x86)\*";
Merge-CIPolicy -OutputFilePath $ResultPolicy -PolicyPaths $SourcePolicies -Rules $PathRules
Set-CIPolicyIdInfo -FilePath $ResultPolicy -ResetPolicyID
```

### 3) Set policy rules**
```powershell
Set-RuleOption -FilePath $ResultPolicy -Option 0          # Enable UMCI
Set-RuleOption -FilePath $ResultPolicy -Option 2          # Require WHQL
Set-RuleOption -FilePath $ResultPolicy -Option 3 -Delete  # Disable Audit Mode
Set-RuleOption -FilePath $ResultPolicy -Option 4          # Disable Flight Signing
Set-RuleOption -FilePath $ResultPolicy -Option 5 -Delete  # Disable Inherit Default Policy
Set-RuleOption -FilePath $ResultPolicy -Option 6          # Enable Unsigned System Integrity Policy
Set-RuleOption -FilePath $ResultPolicy -Option 8          # Require EV Signers
Set-RuleOption -FilePath $ResultPolicy -Option 10 -Delete # Disable Boot Audit on Failure
Set-RuleOption -FilePath $ResultPolicy -Option 11 -Delete # Enable Script Enforcement
Set-RuleOption -FilePath $ResultPolicy -Option 12         # Require Enforce Store Applications
Set-RuleOption -FilePath $ResultPolicy -Option 13 -Delete # Disable Managed Installer
Set-RuleOption -FilePath $ResultPolicy -Option 14 -Delete # Disable Intelligent Security Graph Authorization
Set-RuleOption -FilePath $ResultPolicy -Option 17 -Delete # Disable Allow Supplemental Policies
Set-RuleOption -FilePath $ResultPolicy -Option 18 -Delete # Enable Runtime FilePath Rule Protection
Set-RuleOption -FilePath $ResultPolicy -Option 19         # Enable Dynamic Code Security
```

### 4) Covert the policy into binary**
```powershell
ConvertFrom-CIPolicy $ResultPolicy "SIPolicy.p7b"
```

### 5) Deploy on local machine (Skip this part if deploy by MDM)**
```powershell
Copy-Item "SIPolicy.p7b" -Destination "C:\Windows\System32\CodeIntegrity"
```

### 6) Deploy by MDM**
```
OMA-URI: ./Vendor/MSFT/ApplicationControl/Policies/<Policy GUID>/Policy
Data type: Base64
Certificate file: upload your binary format policy file. You do not need to upload a Base64 file, as Intune will convert the uploaded .bin file to Base64 on your behalf.
Note: Policy GUID can be found in the policy xml as <PolicyID>.
```

# Reference
***
Microsoft recommended block rules

https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/microsoft-recommended-block-rules

Windows Defender Application Control example base policies

https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies

Create a WDAC policy for lightly-managed devices

https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/create-wdac-policy-for-lightly-managed-devices

Understand WDAC policy rules and file rules

https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/select-types-of-rules-to-create

Merge Windows Defender Application Control policies

https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/merge-windows-defender-application-control-policies