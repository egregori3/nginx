# nginx Configuration


# gunicorn Configuration

## NGINX

**http://unix:/home/ubuntu/djangoagent/mysite.sock** is the connection between NGINX and gunicorn

```
   location / 
    {
            include proxy_params;
            proxy_pass http://unix:/home/ubuntu/djangoagent/mysite.sock;
    }
```

## GUNICORN

**/home/ubuntu/djangoagent mysite.wsgi** is the connection between django and gunicorn


## Start in directory containing mysite directory

```
(djangoagent) eric@ubuntu:~/Desktop/djangoagent$ gunicorn --bind unix:/home/eric/Desktop/djangoagent/mysite.sock mysite.wsgi
```

## Start from anywhere 

```
gunicorn --bind unix:/home/ubuntu/djangoagent/mysite.sock --pythonpath /home/ubuntu/djangoagent mysite.wsgi
or
gunicorn -D -w 3 --bind unix:/home/ubuntu/djangoagent/mysite.sock --pythonpath /home/ubuntu/djangoagent mysite.wsgi
or
gunicorn --bind unix:/home/ubuntu/djangotrainer/mysite.sock --pythonpath /home/ubuntu/djangotrainer mysite.wsgi
```






