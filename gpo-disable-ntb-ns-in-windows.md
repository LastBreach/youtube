# Disable NBT-NS

Dieses Skript via GPO als Startskript verteilen.

**disable-nbt-ns.ps1**
```
$regkey = "HKLM:SYSTEM\CurrentControlSet\services\NetBT\Parameters\Interfaces"
Get-ChildItem $regkey |foreach { Set-ItemProperty -Path "$regkey\$($_.pschildname)" -Name NetbiosOptions -Value 2 -Verbose}
```

Erfordert einen Neustart der PCs in der Domäne.
