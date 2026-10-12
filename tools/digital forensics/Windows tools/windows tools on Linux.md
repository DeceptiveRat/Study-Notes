1. install .NET
- install prerequisite

```sh
sudo apt install -y wget apt-transport-https software-properties-common
```

- install .NET9

```sh
wget https://builds.dotnet.microsoft.com/dotnet/scripts/v1/dotnet-install.sh -O /tmp/dotnet-install.sh
chmod +x /tmp/dotnet-install.sh
/tmp/dotnet-install.sh --channel 9.0
rm -r /tmp/dotnet-install.sh
```

- create alias and reload shell

```sh
alias dotnet='~/.dotnet/dotnet'
source ~/.bashrc
```


2. download EZ tools
- download EZ tool

```sh
wget https://download.ericzimmermanstools.com/net9/MFTECmd.zip -O /tmp/MFTECmd.zip
sudo unzip /tmp/MFTECmd.zip -d /opt/MFTEcmd
rm -r /tmp/MFTECmd.zip
```

- add alias

```sh
alias mftecmd='dotnet /opt/MFTEcmd/MFTECmd.dll'
source ~/.bashrc
```


reference:
- (Seth Enoka, 2025/04/23) Running EZ Tools Natively on Linux: A Step-by-Step Guide, 2026/03/12, <https://www.sans.org/blog/running-ez-tools-natively-on-linux-a-step-by-step-guide>