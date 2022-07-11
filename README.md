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
12. fill "Security group name" with "web-server-sg"
13. on "description" fill with "Allow SSH"
14. then click "launch instance"
15. on "instance", check the instance then click "connect"
16. AWS CLI will appear
17. write command " git clone https://github.com/CalvynSatria/Web-Dasar.git"
18. "cd Web-Dasar"
19. install node.js with nvm tools "curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash" 
20. "exit"
21. connect again with the same instance
22. "nvm install v14.15.4"
23. "cd Web-Dasar"
24. install dependencies web server node.js "npm install"
25. "npm run start"
###


#OR
1. Navigate S3
2. click create bucket
3. bucket name "myyy-bucket"
4. for region, choose "app-southeast-1"
5. 

###



<!---
CalvynSatria/CalvynSatria is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
