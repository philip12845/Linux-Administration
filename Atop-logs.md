# Setup logging with ATOP
#### This is still being written and refined

---

# Install and configure atop on Ubuntu

To install atop use  ```apt install atop -y```

## Configure logging interval

Next you may want to increase the amount that atop logs this can be done by editing the config file within ```/usr/share/atop/atop.daily```

You could manually edit this file however thats boring just use sed for text replacement for example this command ```sed -i 's/600/60/g' /usr/share/atop/atop.daily``` This command replaces the 600 with a 60 see more about sed here (https://linux.die.net/man/1/sed)

Next we need to enable the service on startup so use ```systemctl enable atop```

We also need to enable atop timer on startup for log rotate ```systemctl enable atop-rotate.timer```

Im not sure if atop needs a restart after the configuration change above so its probably best to restart it with ```systemctl restart atop```

## A one liner for all of this:

```apt install atop -y && sed -i 's/600/60/g' /usr/share/atop/atop.daily && systemctl enable atop atop-rotate.timer && systemctl restart atop atop-rotate.timer```

---

# Install and configure atop on RHEL / CentOS

To install atop use ```yum install atop -y```

### Configure logging interval

Next you may want to increase the amount that atop logs this can be done by editing the config file within ```/etc/sysconfig/atop```

You could manually edit this file however thats boring just use sed for text replacement for example this command ```sed -i 's/600/60/g' /etc/sysconfig/atop``` This command replaces the 600 with a 60 see more about sed here (https://linux.die.net/man/1/sed)

Next we need to enable the service on startup so use ```systemctl enable atop```

We also need to enable atop timer on startup for log rotate ```systemctl enable atop-rotate.timer```

Im not sure if atop needs a restart after the configuration change above so its probably best to restart it with ```systemctl restart atop```

## A one liner for all of this:

```yum install atop -y && sed -i 's/600/60/g' /etc/sysconfig/atop && systemctl enable atop atop-rotate.timer && systemctl restart atop atop-rotate.timer```

---

# Install and configure atop on Legacy RHEL and CentOS (Before Systemd was added for service management)
