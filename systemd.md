# Systemd
## General
### List uints:
`systemctl list-units` list-units is default option so `systemctl` is sufficient

### Status of a unit:
`systemctl status unit`

### Start, Stop and restart a *unit*:
`systemctl start uint`\
`systemctl stop uint`\
`systemctl restart uint`

### Reload configuration after changes:
`systemctl reload unit` reloads just the config of *unit*\
`systemctl deamon-reload` reloads all unit configurations

### Adding Unit to systemd
directorys: /etc/systemd/system
This is where the sys-admin puts systemwide unit files. Since I am the sys-admin on my machine it is ok to put them here.
But arch(maybe other distros as well) offers a per-user instance of systemd. 
To use this put the unit files in the following directory: 
~/.config/systemd/user

### Enabling
If the uint shall be started automatically after startup it must be enabled.\
`systemctl enable unit` as root\
Enable it and start it immediatly:\
`systemctl enable --now unit` as root

### Example
```bash
# Executes script after wpan0 is available.
# If the script fails, it is retried after 10 seconds and a total of 5 times.

[Unit]
Description=OpenThread Network Setup
ConditionPathExists=/usr/sbin/ot-net-setup.sh
StartLimitIntervalSec=500
StartLimitBurst=5
Wants=example.service
After=network.target

[Service]
Type=simple
Restart=on-failure
RestartSec=10
ExecStart=/usr/sbin/ot-net-setup.sh

[Install]
WantedBy=sys-subsystem-net-devices-wpan0.device
```
For more information about systemd consult the arch wiki [systemd/user](https://wiki.archlinux.org/title/systemd/User) [systemd](https://wiki.archlinux.org/title/Systemd#Writing_unit_files)
or that book you own... how linux works.
