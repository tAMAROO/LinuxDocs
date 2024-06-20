##  Show Device:

```$sudo nmcui device```

##### Output:
```
DEVICE  TYPE      STATE      CONNECTION

{device name}  ethernet  connected  {device name}

lo      loopback  unmanaged  --
```

##  Editing existing connection:

```
$ sudo nmcli con modify '{device name}' ifname {device name} ipv4.method manual ipv4.addresses {IP address}/24 gw4 {Gateway address}
$ sudo nmcli con modify '{device name}' ipv4.dns {DNS address}
$ sudo nmcli con down '{device name}'
$ sudo nmcli con up '{device name}'
```

##  Check that the change was made:

```
$ ip a show {device name}
```

## Notes:

Change anything with {} around it. For instance {device name} is your device that is shown in the command ```$ sudo nmcui device``` and should be changed in the "Editing existing connection" section.

## Research assets:

URL: https://www.linuxtechi.com/set-static-ip-address-on-rhel-9/
