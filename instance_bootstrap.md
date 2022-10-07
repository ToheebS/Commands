


``` js
#!/bin/bash
yum update -y
yum install -y httpd
systemctl enable httpdsystemctl start httpd


MYINSTANCE=$(curl -s http://169.254.169.254/latest/meta-data/instance-id)
MYADDRESS=$(curl -s http://169.254.169.254/latest/meta-data/public-ipv4)
EC2_AVAIL_ZONE=$(curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone)

echo "<h1>Hello World from $MYADDRESS  </h1>" >> /var/www/html/index.html
echo "<h1>Chilling in AZ $EC2_AVAIL_ZONE</h1>" >> /var/www/html/index.html
echo "<h1>Instance ID $MYINSTANCE </h1>" >> /var/www/html/index.html

======================================================================
systemctl status httpd 

echo "<h1>Hello World from Instance B</h1>" > /var/www/html/index.html

```