# PureWeb® AWS EC2 Scheduler

Requires creation of Amazon Linux AMI to run the script ec2_operator_pureweb_design.py at a set interval (5 minutes to allow the instances time to start/stop)

Paste the contents of pureweb-design-ec2-scheduler in this repository into the User Data field when creating the instance. This uses PIP to install the required modules.

![User Data Text](https://cloud.githubusercontent.com/assets/9810259/7376015/db8c1d62-ed99-11e4-8c22-edd58b092551.png)

Amazon Linux AMI also requires IAM Role that has the ability to start/stop and describe EC2 instances. Current example IAM Role for reference is called "pureweb-design-ec2-scheduler".

To mark EC2 instances for startup / shutdown attach tags use the tag keys "auto:start" and "auto:stop". Note times are in UTC using cron format  e.g. "10 13 * * 1-5"  is UTC format so 13:10 means start up between 06:00 and 06:10MST Monday to Friday. 

![Example auto:stop and auto:start tags](https://cloud.githubusercontent.com/assets/9810259/7376097/98b17856-ed9a-11e4-8775-9919f79003b9.png)

**Note:** due to the time it takes to start and stop instances:
* Starts up instances that have an `auto:start` time in the next 10 minutes
* Stops instances that have an `auto:stop` falling between now and 10 minutes ago
