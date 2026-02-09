# Windows Subsystem for Linux

## Installing

In PowerShell:

```
wsl --install   # will install Ubuntu by default
```

To install Fedora:

```
wsl --install FedoraLinux-43
```

To choose from other distros:

```
wsl --install --no-distribution
wsl --list --online
```

## List installed distros

```
wsl --list --verbose    # --verbose is optional
```

## Check WSL version

```
wsl --version
```

## Update WSL

```
wsl --update
```

## Check WSL status

```
wsl --status
```

## Terminate

```
wsl --terminate <distro name>
```

## Shutdown (terminate all running distros)

```
wsl --shutdown
```

## Uninstall a distro

```
wsl --unregister <distro name>
```

## Windows Terminal customization

In the settings JSON file:

```
"profiles":
{
    "defaults": 
    {
        "colorScheme": "One Half Dark",
        "opacity": 50,
        "useAcrylic": true
    }
}
```