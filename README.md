# PureWeb® AWS EC2 Scheduler

Requires creation of Amazon Linux AMI to run the script ec2_operator_pureweb_design.py at a set interval (5 minutes to allow the instances time to start/stop)

Paste the contents of pureweb-design-ec2-scheduler in this repository into the User Data field when creating the instance. This uses PIP to install the required modules.

Amazon Linux AMI also requires IAM Role that has the ability to start/stop and describe EC2 instances. Current example IAM Role for reference is called "pureweb-design-ec2-scheduler".

To mark EC2 instances for startup / shutdown attach tags use the tag keys "auto:start" and "auto:stop". Note times are in UTC using cron format  e.g. "10 13 * * 1-5"  is UTC format so 13:10 means start up between 06:00 and 06:10MST Monday to Friday.
