Create a simple website using HTML5, CSS3 & JavaScript
I'm trying use AWS to deploy this simple website


***Setting AWS***

### VPC Setting
1. Log-in to AWS
2. Search VPC on search box
3. Create New VPC
4. Resource to create, choose "VPC Only"
5. Name VPC "my-vpc-1"
6. IPv4 CIDR block, choose "IPv4 CIDR manual input"
7. Fill IPv4 CIDR box with "10.0.0.0/16"
8. IPv6 CIDR block, choose "No IPv6 CIDR block"
9.For Tenancy, i choose default
10. Click on create VPC
###

### Internet Gateway
1. Click "Internet Gateways" on VPC Menu
2. CLick "Create internet Gateway"
3. Fill name tag "my-gateway"
4. Click "Create internet gateway"
5. Then the "attach to a VPC" will appear above the vpc menu page
6. click "attach to a VPC"
7. On Available VPCs, select ".... my-vpc-1"
8. CLick "attach internet gateway"
###

### Subnet
1. Click "Subnets" on VPC menu
2. Click "Create Subnet"
3. On VPC ID, Select "my-vpc-1"
4. Subnet name "my-subnet-1"
5. Availability Zone, select "ap-southeast-1a (Asia Pacific-Singapore)"
6. Fill IPv4 CIDR block with "10.0.0.0/24"
7. Click "add new subnet"
8. Subnet name "my-subnet-2"
9. Availability Zone, select "ap-southeast-1b (Asia Pacific-Singapore)"
10. Fill IPv4 CIDR block with "10.0.1.0/24"
11. Then, click create 
###

### Route Table
1. Click "Route Table" on VPC menu
2. Click "Create Route Table"
3. Route table name "my-route-table-1"
4. On VPC, select "my-vpc-1"
5. Click "create route table"
6. on my-route-table-1, click "actions", then "Edit subnet associations"
7. On Edit subnet associations, select/check "my-subnet-1" box
8. Save associations
9. Back to "Route Tables"
10. Click "Create Route Table"
11. Route table name "my-route-table-2"
12. On VPC, select "my-vpc-1"
13. Click "create route table"
14. on my-route-table-2, click "actions", then "Edit subnet associations"
15. On Edit subnet associations, select/check "my-subnet-2" box
16. Save associations
17. Back to route table
18. click "my-vpc-1" check box
19. click tab "routes"
20. click "edit routes"
21. click "add route"
22. fill destination with "0.0.0.0/0"
23. on target, click "Internet Gateway" then click "my-gateway"
24. click "save changes"
###

###Launch Instance
1. Search "ec2" on search bar
2. click "instance" on ec2 menu
3. click "launch instance"
4. on quick start, choose "ubuntu" with "Ubuntu Server 22.04 LTS"
5. on "instance type" choose "t2.micro"
6. on "key pair", choose "Proceed without a key pair"
7. click edit on "network setting"
8. on vpc, choose "my-vpc-1"
9. on subnet, choose "my-subnet-1"
10. on "Auto-assign Public IP" choose "enable"
11. for security group (still on network setting), click "create security group"
12. fill "Security group name" with "web-server-nginx-sg"
13. on "description" fill with "Allow SSH"
14. then click "launch instance"
15. on "instance", check the instance then click "connect"
16. AWS CLI will appear
17. write command "git clone https://github.com/dicodingacademy/a387-jarkom-labs.git"
18. "cd a387-jarkom-labs/"
19. install node.js with nvm tools "curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash" 
20. "exit"
21. connect again with the same instance
22. "nvm install v14.15.4"
23. "cd a387-jarkom-labs/"
24. install dependencies web server node.js "npm install"
25. "npm run start"
###


#Edit Inbound Rules
1. Click instance
2. go to security tab
3. edit inbound rules
4. add rules
5. choose "Custom TCP" and fill "8000" on port range
6. choose "Anywhere-IPv4" in source
7. save rules
8. back to instance, connect, "cd a387-jarkom-labs/" then "npm run start"
9. run with "ip public:8000"

#Install NGINX
1. "sudo apt update"
2. "sudo apt-get install nginx -y"
3. "sudo systemctl status nginx" to chek nginx status
4. go to "security groups"
5. check the web-server-nginx-sg, then click edit inbound rules
6. add rules "http" , "anywhere-IPv4" and "https" , "anywhere-IPv4"
7. connect to instance 
8. "cat /etc/nginx/sites-available/default"
9. "sudo nano /etc/nginx/sites-available/default"
      proxy_pass http://localhost:8000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
    
10. delet "# First attempt to serve request as file, then
# as directory, then fall back to displaying a 404.
try_files $uri $uri/ =404;"

11.Ctrl X +Y+enter
12. "sudo systemctl restart nginx"
13. "cd a387-jarkom-labs/"
14. "npm run start"


#Limit access (prevent DDOS)
1. "sudo nano /etc/nginx/sites-available/default"
{2. "limit_req_zone $binary_remote_addr zone=one:10m rate=30r/m;" before server
3. "limit_req zone=one;" on location
4. ctrl x + y + enter
5. "sudo systemctl restart nginx"} ----> Fail
6. "a387-jarkom-labs/"
7. " sudo nano app.js"
8. change "Hello world!" to Calvyn Chandra Satria







<!---
CalvynSatria/CalvynSatria is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
