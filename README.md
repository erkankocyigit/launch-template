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
    ```
    #!/bin/bash
    apt update -y
    apt install nginx -y
    cd /var/www/html
    git clone https://github.com/zce/html5up.git
    cp -r html5up/arcana/* .
    service nginx start
    ```
# <h3>Auto Scaling Groups</h3>
- Name — demo-asg
- Launch Template — demo-lt
- Next
- Vpc — default
- Availability zones and subnets — us-east-1a
- Next
- Load Balancing — Attach to a new load balancer
- Application Load Balancer
- Load balancer name—demo-lb
- Load balancer scheme—Internet-facing
- Availabilitiy zones and subnets—us-east-1b (its for second)
- Port-80——>>Default routing(forward to)—create target group—>new target group  name—demo-tg
- Next 
- Desired capacity-2—>Minimum capacityi-1——>Maximum capacity-3
- Scaling policies—Target tracking scaling policy—>Target value-30
- _For verify—Load Balancers—click demo-lb —->>DNS name copy and paste safari_
  _(it didn’t work)_
- _Go to security groups— select default-edit inbound rules—add rules_
- _Type-SSh—— port range-22——source type-anywhere-IPv4_
- _Type-Custom TCP——port range-80———source type-Anywhere-IPv4_


