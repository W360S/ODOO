~# ODOO
Install odoo

setup basic VPS with ubuntu

~# apt-get update && apt-get upgrade -y

Install nodejs

~# curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

~# sudo apt-get install -y nodejs

~# apt-get update && apt-get upgrade -y

~# wget -O - https://nightly.odoo.com/odoo.key | apt-key add -

~# echo "deb http://nightly.odoo.com/9.0/nightly/deb/ ./" >> /etc/apt/sources.list

~# apt-get update && apt-get upgrade -y

~# apt-get install odoo -y

config runing port 80 & 443

~# vim /etc/rc.local

add 2 line bellow at the end of rc.local

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8069

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 443 -j REDIRECT --to-port 8070

then save

Configure Apache Web Server with Odoo

~# apt-get update && apt-get upgrade -y

~# sudo apt-get install apache2 -y

After installing apache on your machine, you need to enable some modes by executing below commands.
 
~# sudo a2enmod proxy proxy_http

do following the tutorial http://www.surekhatech.com/blog/configure-apache-web-server-with-odoo

Enable odoo data filter

~# cd /etc/odoo/ && vim openerp-server.conf

Find replace 2 line below

dbfilter = ^%h$

list_db = False

then save

Download & Settup wkhtmltopdf

Remove existing installation if settup before & error

~# sudo apt-get remove --purge wkhtmltopdf

~# sudo apt-get autoremove --purge wkhtmltopdf -y

Download wkhtmltopdf patched with qt using below command
sudo wget -P Downloads https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.1/wkhtmltox-0.12.1_linux-trusty-amd64.deb

or other sources store here:
sudo wget -P Downloads http://download.gna.org/wkhtmltopdf/0.12/0.12.1/wkhtmltox-0.12.1_linux-trusty-amd64.deb

replace "trusty" with your OS name (Your VPS Name) and if 64 bit only then keep "amd64" like that, otherwise change it to "i386" and down load the deb file.

After that execute the following commands,

cd ~/Downloads

~# sudo dpkg -i wkhtmltox-0.12.1_linux-trusty-amd64.deb

Now, check wkhtmltopdf version with below command,

wkhtmltopdf -V
