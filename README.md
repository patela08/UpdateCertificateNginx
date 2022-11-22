# UpdateCertificateNginx
How to replace certificate on NGINX running on EC2 


## Change Certificate on Ubuntu ngInx

### Login to Instance:

`ssh -i efh-prod.pem ubuntu@ec2-adf.ap-east-1.compute.amazonaws.com`

## Create New dir:

`/etc/nginx/ssl$ mkdir 20220927`

## Copy certificate and private key: (To new created dir):

```
cp -i efh-prod.pem /Users/usename/Downloads/interm.cer ubuntu@ec2-adf.ap-east-1.compute.amazonaws.com:/etc/nginx/ssl/20220927

scp -i efh-prod.pem /Users/usename/Downloads/org_cert.cer ubuntu@ec2-adf.ap-east-1.compute.amazonaws.com:/etc/nginx/ssl/20220927

scp -i efh-prod.pem /Users/usename/Downloads/org.key ubuntu@ec2-adf.ap-east-1.compute.amazonaws.com:/etc/nginx/ssl/20220927
```


## Create New Combine Certificate cert with interm cert in a new dir:

`sudo cat org_cert.cer interm.cer >> org.cer`

## Change Certificate in config file:

`sudo nano /etc/nginx/conf.d/efh.conf`

## Check Syntax and restart:

```
sudo nginx -t
sudo systemctl restart nginx
```

