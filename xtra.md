###
---

> Try to run the following two commands:
```
sudo fuser -k 80/tcp
```
```
sudo fuser -k 443/tcp
```
And then execute
```
sudo service nginx restart
```

> Test Nginx and the Nginx Reverse Proxy

Lastly, we need to run an Nginx configuration test and restart Nginx to check its performance. 
Type the below command to verify the Nginx functioning on the Linux terminal:
```
service nginx configtest
```

```
service nginx restart
```
Remember, if you receive a failed test, that most likely indicates that Apache was not properly set up.
```
apachectl configtest
```
