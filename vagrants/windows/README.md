# Windows Server 2019 + SQL Server
For [SQL Server Vagrant](https://app.vagrantup.com/gusztavvargadr/boxes/sql-server) we need to run the following commands for creating instance:

```sh
$ vagrant up
```

Setup Ansible Host:

* [OpenSSH Server Configuration for Windows](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_server_configuration)
* [Setting up a Windows Host](https://docs.ansible.com/ansible/latest/user_guide/windows_setup.html)
* [Windows performance](https://docs.ansible.com/ansible/latest/user_guide/windows_performance.html)

```ps1
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$url = "https://raw.githubusercontent.com/jborean93/ansible-windows/master/scripts/Upgrade-PowerShell.ps1"
$file = "$env:temp\Upgrade-PowerShell.ps1"
$username = "vagrant"
$password = "vagrant"

(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force

# Version can be 3.0, 4.0 or 5.1
&$file -Version 5.1 -Username $username -Password $password -Verbose

$reg_winlogon_path = "HKLM:\Software\Microsoft\Windows NT\CurrentVersion\Winlogon"
Set-ItemProperty -Path $reg_winlogon_path -Name AutoAdminLogon -Value 0
Remove-ItemProperty -Path $reg_winlogon_path -Name DefaultUserName -ErrorAction SilentlyContinue
Remove-ItemProperty -Path $reg_winlogon_path -Name DefaultPassword -ErrorAction SilentlyContinue

[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$url = "https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1"
$file = "$env:temp\ConfigureRemotingForAnsible.ps1"

(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)

powershell.exe -ExecutionPolicy ByPass -File $file
```

Check WinRM services:
```sh
$ winrm enumerate winrm/config/Listener
```


Database Engine:

* Windows Authentication with user `vagrant\vagrant`.
* SQL Server Authentication with user `sa` and password `Vagrant42`.