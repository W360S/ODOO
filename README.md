# ODOO
Install odoo

setup basic VPS with ubuntu

apt-get update && upgrade -y

Install nodejs

curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
apt-get update && apt-get upgrade -y

# wget -O - https://nightly.odoo.com/odoo.key | apt-key add -
# echo "deb http://nightly.odoo.com/9.0/nightly/deb/ ./" >> /etc/apt/sources.list
# apt-get update && apt-get install odoo
