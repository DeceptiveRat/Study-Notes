## setup and status
- `ufw status` : check status
- `ufw status verbose`: detailed status
- `ufw enable`
- `ufw disable`
- `ufw reset`: disables UFW and deletes custom rules

## default policies
- `ufw default deny incoming`
- `ufw default allow outgoing`

## managing rules
- `ufw allow <port>`
- `ufw allow <port>/<protocol>`: allow protocol on port
- `ufw allow <port1>:<port2>/<tcp/udp>`: allow protocol on ports
- `ufw deny <port>`: silently drop traffic on port
- `ufw reject <port>`: drop traffic and send "connection refused" response to sender
- `ufw allow <service>`: (e.g. `ufw allow http`)
- `ufw allow from <ip>`
- `ufw allow from <ip> to any port <port>`
- `ufw allow from <ip>/24`: (e.g. `ufw allow from 192.168.1.0/24`)

## advanced rule management
- `ufw status numbered`: view numbered rules
- `ufw delete <rule number>`
- `ufw insert <number> <rule>`: (e.g. `ufw insert 1 allow from 192.168.1.100`)

## application profiles
- `ufw app list`: list profiles
- `ufw app info <app>`: (e.g. `ufw app info "Nginx Full"`)
- `ufw allow <app>`

## debugging
- `ufw logging on`: enable logging to `/var/log/ufw.log`
- `ufw logging <low|medium|high|full>`: set verbosity