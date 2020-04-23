# Nginx Setup

## GeoIp2 setup

1. Install geoIp2 module package, with mmdblookup utility.  `sudo apt-get install libnginx-mod-http-geoip2 mmdb-bin`.

2. Download GeoliteDBs , also included here in the *assets/* folder.

3. Copy contents of compressed geolite dbs in folder */usr/share/nginx/geoIP2/*

4. Copy `geoip.conf` to folder */etc/nginx/conf.d/*

## OpenTracing Setup

*Links:*

 - (nginx-opentracing module)[https://github.com/opentracing-contrib/nginx-opentracing]
 - (opentracing-nginx blog)[https://www.nginx.com/blog/opentracing-nginx-plus/]

*Steps:*

1. Install nginx opentracing module , substitute `NGINX_VERSION` below with your nginx version,
   copy the `*.so` to your nginx --prefix modules folder , for me its `/usr/share/nginx/modules`

  ```
    wget https://github.com/opentracing-contrib/nginx-opentracing/releases/download/v0.9.0/linux-amd64-nginx-${NGINX_VERSION}-ngx_http_module.so.tgz
    tar zxf linux-amd64-nginx-${NGINX_VERSION}-ngx_http_module.so.tgz -C /usr/share/nginx/modules/
  ```

2. Load the module using `load_module` directive in the top‑level (main) context of your nginx.conf configuration file:
   `load_module modules/ngx_http_opentracing_module.so`

3. Load and configure your tracer libs in your nginx directives, see (opentracing.conf)[/opentracing.conf] example using jaeger