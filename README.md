# ODOO
Install odoo

setup basic VPS with ubuntu

apt-get update && upgrade -y

Install nodejs

$ curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

$ sudo apt-get install -y nodejs

$ apt-get update && apt-get upgrade -y

$ wget -O - https://nightly.odoo.com/odoo.key | apt-key add -

$ echo "deb http://nightly.odoo.com/9.0/nightly/deb/ ./" >> /etc/apt/sources.list

$ apt-get update && apt-get install odoo

config runing port 80 & 443

$ vim /etc/rc.local

add 2 line bellow at the end of rc.local

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8069

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 443 -j REDIRECT --to-port 8070
