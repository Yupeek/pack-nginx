pack-nginx
==========

Shinken configuration pack for Nginx status check.

it use the nginx module [HttpStubStatusModule](http://nginx.org/en/docs/http/ngx_http_stub_status_module.html)
to check a nginx server load. 

it provide:

- number of active Connections
- number of Connections by state (reading, waiting or writing)
- number of request/s
- number of Connections/s
- number of request/Connections


shipped with a graphite template and the check_nginx_status.pl script.




### nginx configuration

inside your server {} block, add a location /nginx_status

    location /nginx_status {
          stub_status on;
          access_log   off;
          allow 1.1.1.1;  # fix your ip range ie: 172.31.0.0/16 or 192.168.1.0/24
          deny all;
    }


### shinken configuration

add to your host the `nginx` template 
	
	define host{
        use                     ... ,nginx
 		...
 		# facultative config.
 		
 		
	}
	
### credit


this pack is in fact just the formalisation of the script proposed by sysNove in 
https://www.sysnove.fr/blog/2014/02/supervision-nginx-shinken.html