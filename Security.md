# Firewall configuration:

## Create a new zone:

```firewall-cmd --permanent --new-zone=zone-name```

### Reload the new zone:

```firewall-cmd --reload```

### Make the new settings persistent:

```firewall-cmd --runtime-to-permanent```

## Set default zone:

### Display the current default zone:

```firewall-cmd --get-default-zone```

### Set the new default zone:

```firewall-cmd --set-default-zone zone-name```

## Set default target:

### Set target to drop:
```firewall-cmd --permanent --zone=Your_Zone_Here --set-target=DROP```

```firewall-cmd --reload```

## After firewall changes:

### Run updates to system:
```sudo dnf update```

# ClamAV 

### Install ClamAV:
```sudo dnf upgrade --refresh```

```sudo dnf install clamav clamd clamav-update```

### Update ClamAV:
```sudo systemctl stop clamav-freshclam```

```sudo freshclam```

```sudo systemctl enable clamav-freshclam --now```

### Install ClamTK:
```sudo dnf install clamtk```

# Check Status of SELinux:

```sestatus```

