---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: ''
datePublished: '2016-02-28T14:11:25.613Z'
dateModified: '2016-02-28T14:11:21.897Z'
title: Deploying Node.js app to AWS Elastic Beanstalk
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-02-28-deploying-nodejs-app-to-aws-elastic-beanstalk.md
published: true
url: deploying-nodejs-app-to-aws-elastic-beanstalk/index.html
_type: Article

---
# Deploying Node.js app to AWS Elastic Beanstalk

1\. Login to [AWS Console][0].

2\. Create an IAM user to get an access token for use with AWS EB CLI
![AWS Console](https://s3-us-west-2.amazonaws.com/the-grid-img/p/4837ce4618403ef09d995391c6b4d466e9a94021.png)
![Create new user](https://the-grid-user-content.s3-us-west-2.amazonaws.com/693e3e14-88e1-435a-92a8-bb8a48b2c0ca.png)
![Choose username](https://the-grid-user-content.s3-us-west-2.amazonaws.com/24230975-c4e4-40ae-91bd-a8d9697668fb.png)
![Save access key and secret](https://the-grid-user-content.s3-us-west-2.amazonaws.com/fec1618d-b040-4636-8eba-11724dbd1434.png)
![Attach policy to the newly created user](https://the-grid-user-content.s3-us-west-2.amazonaws.com/c6654700-f5b5-438d-ad7c-b45bf536fddf.png)
![Grant admin access for demo purpose](https://s3-us-west-2.amazonaws.com/the-grid-img/p/165d08cee1c4743766262f38a94f85541f7f0a8e.png)

3\. Install and configure AWS EB CLI, follow instructions in the [AWS EB CLI documentation][1].

4\. Run following commands in your Node.js project.

* _eb init_
* _eb __create_
* _eb deploy_

_eb init_ will initialise an application in Elastic Beanstalk (EB), which basically contains multiple environments.

_eb create_ creates an environment, such as development, staging or production environment. Creating an environment in EB will create an EC2 instance with appropriate Security Group and Elastic Block Store, also enables auto scaling with Elastic Load Balancer. On top of that logging and metrics are enabled by default which can be seen in CloudWatch.

_eb deploy_ will copy your project into the EC2 instance, install the dependencies and start your webapp. EB by default will run _main.js_, _server.js_, or _npm star__t _in that order.

5\. Run _eb open_ to open your webapp. Should you unable to access your app, run _eb logs_ to see the errors.

# Creating database in AWS RDS

1\. Login to [AWS Console][0].

2\. Click on RDS under Database category, and click Get Started.

3\. Follow the instructions to create the database you need.

4\. After creating the RDS instance, click on it to see the details, you should see the endpoint shown in the image below. Use the endpoint in your Node.js app to access the database. If you cannot access it, make sure the security group that you are using has an inbound rule to allow the port your database is using. For more information on troubleshooting, see this [awesome guide][2] by AWS.
![RDS Endpoint](https://the-grid-user-content.s3-us-west-2.amazonaws.com/06842fa0-0300-4488-9cc6-038aba0718ca.png)

# Creating a Redis cluster using AWS ElastiCache

Read on if you're using in-memory datastore or cache in your app.

1\. Login to [AWS Console][0].

2\. Click on ElastiCache under Database category.

3\. Click on Launch Cluster Group and follow the instructions to launch an Redis cluster.

4\. To get the endpoint of the Redis node that you just created, see the image below.
![Redis node endpoint](https://the-grid-user-content.s3-us-west-2.amazonaws.com/c8995722-589d-4863-a940-caed6f2a9028.png)

[0]: https://console.aws.amazon.com/
[1]: http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html
[2]: http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Troubleshooting.html