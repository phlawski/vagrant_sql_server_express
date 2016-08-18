# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<'SCRIPT'
  sqlcmd -Q "CREATE DATABASE hybris"
  sqlcmd -d hybris -Q "CREATE USER [vagrant] FROM LOGIN [vagrant]"
  sqlcmd -d hybris -Q "EXEC sp_addrolemember N'db_owner', N'vagrant'"
  sqlcmd -d hybris -Q "ALTER DATABASE hybris SET READ_COMMITTED_SNAPSHOT ON"
  sqlcmd -d hybris -Q "ALTER DATABASE hybris SET ALLOW_SNAPSHOT_ISOLATION ON"
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "msabramo/mssqlserver2014express"
  config.vm.provision "shell", inline: $script
end
