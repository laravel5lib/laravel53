# Laravel 5.3
```
server {
        listen       80;
        server_name  laravel53.dev;
        root   "D:/laravel53/public";
	index  index.html index.htm index.php;
        location / {
	    try_files $uri $uri/ /index.php?$query_string;
            #autoindex  on;
        }
        location ~ \.php(.*)$ {
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_split_path_info  ^((?U).+\.php)(/?.+)$;
	    #fastcgi_split_path_info       ^(.+\.php)(/.+)$;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            fastcgi_param  PATH_INFO  $fastcgi_path_info;
            fastcgi_param  PATH_TRANSLATED  $document_root$fastcgi_path_info;
            include        fastcgi_params;
        }
}
```