# project-10
CONFIGURE NGINX AS A LOAD BALANCER

I create an EC2 VM based on Ubuntu Server 20.04 LTS and name it Nginx LB (do not forget to open TCP port 80 for HTTP connections, also open TCP port 443 – this port is used for secured HTTPS connections)

I update the instance and Install Nginx. i checked the status and it is running perfectly.

![text1](https://user-images.githubusercontent.com/108102087/195422963-0d060b7f-47ca-4272-a8df-f8432f5ea844.PNG)

I created a domain name using freenon and added the servers cerated by default on routes 53

![text2](https://user-images.githubusercontent.com/108102087/196011321-fa816972-c6e2-4e5c-ac4a-adb4eadc7ad2.PNG)

I also added records on routes 53 to include the domain name using the public ip address of the load_balancer

![text3](https://user-images.githubusercontent.com/108102087/196011368-356a904b-3bdd-4535-95e8-52be01b8bd14.PNG)

I encounted blockers afterwards when i put the domain name to the browser and the result was "error 502 bad gateway"
The error log from sudo cat /var/log/nginx/error.log shows connection failed while connecting to upstream. "http://toolingysf.ml"
and "http://myproject/favicon.ico" I therefore checked the web servers, the httpd is down so i restart httpd

![text4](https://user-images.githubusercontent.com/108102087/196011629-14415d44-f621-4ede-80e1-211689170fa4.PNG)

## REGISTER A NEW DOMAIN NAME AND CONFIGURE SECURED CONNECTION USING SSL/TLS CERTIFICATES

certbot installed

![text5](https://user-images.githubusercontent.com/108102087/196011829-31bcb946-33e7-47db-b5d0-69fd3baddf37.PNG)

The domain site is not previously secured, therefore i downloaded the certificate using
 certbot . how it is secured.
 
 ![text6](https://user-images.githubusercontent.com/108102087/196012058-b16b7523-1aef-4ba9-bf7b-45fcf4c68eab.PNG)
 
 Seting up periodical renewal of your SSL/TLS certificates using the command * */12 * * *   root /usr/bin/certbot renew > /dev/null 2>&1

 
