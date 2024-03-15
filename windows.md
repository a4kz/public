### Install Scoop to a custom directory by changing `SCOOP`

#### Assuming the target directory is `F:\scoop`, in a __PowerShell__ command console, run:

```
$env:SCOOP='F:\scoop'
[environment]::setEnvironmentVariable('SCOOP',$env:SCOOP,'User')
```



### Installing Scoop in __Powershell__
```
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
```
```
iwr -useb get.scoop.sh | iex
```

### Scoop commands
```
scoop help

scoop install curl

scoop search vim

scoop update

scoop update curl

scoop update *
```

### Use a proxy that isn't configured in Internet Options

```
scoop config proxy 127.0.0.1:10809
```


### Uninstalling Scoop

```
scoop uninstall scoop
del .\scoop -Force
```
### Configure Scoop to install global programs to a custom directory by changing `SCOOP_GLOBAL`

#### Assuming the target directory is `F:\scoop_apps`, in an __admin-enabled__ PowerShell command console, run:

```
$env:SCOOP_GLOBAL='F:\scoop_apps'
[Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')
```
```
scoop install -g <app>
```
