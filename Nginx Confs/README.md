# Nginx Setup

## GeoIp2 setup

1. Install geoIp2 module package, with mmdblookup utility.  `sudo apt-get install libnginx-mod-http-geoip2 mmdb-bin`.

2. Download GeoliteDBs , also included here in the *assets/* folder.

3. Copy contents of compressed geolite dbs in folder */usr/share/nginx/geoIP2/*

4. Copy `geoip.conf` to folder */etc/nginx/conf.d/*