sudo mkdir /etc/ssl/nginx

cd /etc/ssl/nginx


sudo cp nginx-repo.crt /etc/ssl/nginx/
sudo cp nginx-repo.key /etc/ssl/nginx/


sudo wget https://cs.nginx.com/static/keys/nginx_signing.key && sudo apt-key add nginx_signing.key
sudo wget https://cs.nginx.com/static/keys/app-protect-security-updates.key && sudo apt-key add app-protect-security-updates.key

sudo apt-get install apt-transport-https lsb-release ca-certificates

printf "deb https://pkgs.nginx.com/plus/ubuntu `lsb_release -cs` nginx-plus\n" | sudo tee /etc/apt/sources.list.d/nginx-plus.list

printf "deb https://pkgs.nginx.com/app-protect/ubuntu `lsb_release -cs` nginx-plus\n" | sudo tee /etc/apt/sources.list.d/nginx-app-protect.list
printf "deb https://pkgs.nginx.com/app-protect-security-updates/ubuntu `lsb_release -cs` nginx-plus\n" | sudo tee -a /etc/apt/sources.list.d/nginx-app-protect.list

sudo wget -P /etc/apt/apt.conf.d https://cs.nginx.com/static/files/90pkgs-nginx

sudo apt-get update

sudo apt-get install -y nginx-plus

sudo apt-get install app-protect app-protect-attack-signatures


nginx -v

----------------------------------------------------------------------------------------
apt-get install nginx-ha-keepalived


nginx-ha-setup


cat /var/run/nginx-ha-keepalived.state


---------------------------------------------------------------------------------------
apt-get install nginx-sync


nano /etc/nginx-sync.conf

NODES="ip"
CONFPATHS="/etc/nginx/nginx.conf /etc/nginx/conf.d /etc/nginx/nap"
EXCLUDE="default.conf"

on master:
sudo ssh-keygen -t rsa -b 2048
sudo cat /root/.ssh/id_rsa.pub


on slave:
sudo mkdir /root/.ssh
echo 'from="10.2.107.40" ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCbE/F55VF7QUSKhYhP10sGELQnjt09cqtBV/ghMEWT6v2wZT9sWP8Mb8tzFiNDHFJ7Uynv+MsNHZ8uH6mVGGNh2a43VPYAjFMDeo6YV6JyoMzR218NidipVoFtXofBYpH9kUdPwuBMv64NYYeGcdVJGyqWg5T8xjcPVS/n9pZLgbAUjO/BscMI1hZ7m6JmFpc+10neh/zQjICEroMxbXP3pL8s9fovBG8GJyLAthxhI/7+ecS4/8o9+tGryEr3iPgomsrT79QrZ93Q4qo11GNCOnSU0qSbwo1vl6NcrRUQ+HCZrWXug5ClzSTLFKUBpXNsF7Ln0XBo/JgB/CNjXjBJ root@user' >> /root/.ssh/authorized_keys

Add the following line to /etc/ssh/sshd_config:

PermitRootLogin without-password



 sudo service ssh reload
