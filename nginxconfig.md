```shell
server {
	listen       8081;
        server_name  0.0.0.0;

        location /api/ {
		client_max_body_size 1024M;
		client_body_buffer_size 1024M;
		proxy_pass http://127.0.0.1:8080/;
		proxy_set_header X-Real $remote_addr;

        }
	location / {
            proxy_pass http://127.0.0.1:9527/;
        }

}


```
