# Launch-Template

# <h3>Creating Launch Template</h3>
- Launch template name: demo-lt
- Quick start — Ubuntu 20.04
- Instance type — t2.micro
- Key pair name — orchsky-demo
- Network settings — subnet-us-east-1e
- Firewall — select existing security group
- Common security groups — default
- Advanced network configuration — auto-assign public ip (enable)
- Advanced details-user data
    `
    #!/bin/bash
    apt update -y
    apt install nginx -y
    cd /var/www/html
    git clone https://github.com/zce/html5up.git
    cp -r html5up/arcana/* .
    service nginx start
    `
    