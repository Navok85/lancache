Configuration NGINX:
===================================
 - Modify every "proxy_bind" variable in every vhosts-enabled/lancache-*.conf with the correct ip configured in /etc/network/interfaces


Ordner anlegen
    sudo mkdir -p /pool1/lancache/data/blizzard/
    sudo mkdir -p /pool1/lancache/data/microsoft/
    sudo mkdir -p /pool1/lancache/data/installs/
    sudo mkdir -p /pool1/lancache/data/other/
    sudo mkdir -p /pool1/lancache/data/tmp/
    sudo mkdir -p /pool1/lancache/data/origin/
    sudo mkdir -p /pool1/lancache/data/steam/
    sudo mkdir -p /pool1/lancache/logs/Errors
    sudo mkdir -p /pool1/lancache/logs/Keys
    sudo mkdir -p /pool1/lancache/logs/Access

