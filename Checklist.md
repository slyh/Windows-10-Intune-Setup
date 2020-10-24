# Checklist

***

### [AppLocker](AppLocker.md)

- Check if [Microsoft Media Creation Tool](https://www.microsoft.com/en-us/software-download/windows10) is able to run in non-allowed locations.

### [Device Installation Restrictions](DeviceInstallationRestrictions.md)

### [Disable Sleep](DisableSleep.md)

- Check if Sleep option appears in power menu.

### [Local Security](LocalSecurity.md)

- Check if Ctrl + Alt + Del is required in elevate actions.
- Check if UAC prompt present when launching Task Manager.

### [WDAC](WDAC.md)

- Check if any executable file in the [block list](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/microsoft-recommended-block-rules) is able to run.

### [Disable delivery optimization](Others.md)

- Check if delivery optimization in Settings is turned off.

### [Windows Hello for Business](Others.md)

- Setup Windows Hello PIN with alphabet.

### [Turn on Credential Guard](Others.md)

- Check VBS and Credential Guard is turned on in System Infromation.

# Settings require manual setup

***

### Require Ctrl + Alt + Del for UAC prompt

**Group Policy**

*Computer Configuration\Administrative Templates\Windows Components\Credential User Interface*

Enable *Require trusted path for credential entry*.

### Windows Firewall

Block all incoming connections.

### Require Windows Hello for Business for local login

**Group Policy**

*Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options*

Enable *Interactive logon: Require Windows Hello for Business or smart card*

### BitLocker

To be filled.