# <ins>Blitz 1 Load Test Report</ins>

September 30, 2023

By:  Khalil Elkharbibi


### <ins>Overview</ins>

Nike has reached out to me regarding the URL shortener deployed on AWS Elastic Beanstalk from ((https://github.com/atlas-lion91/Deployment_3.git)). In their email, Nike expressed concerns raised by their customers about the extended duration it takes for their webpages to load. Nike's request is for us to minimize the latency that customers are currently encountering.

### <ins>Purpose</ins>

The purpose of Blitz 1 was to conduct a rigorous load test on the Python URL Shortening application deployed on AWS Elastic Beanstalk. This involved using Apache JMeter to simulate 1000 requests, allowing us to assess the application's performance and its infrastructure's ability to handle high traffic.


#### 1. <ins>Load Test Execution</ins>

During the blitz, I began by confirming the availability and accessibility of the Python URL Shortening application, hosted on an EC2 instance. Apache JMeter was configured to send 1000 requests to the application's URL simultaneously. Throughout this process, I closely monitored the application's response time to gauge the impact of these requests. It's important to note that both the URL shortening app and Apache JMeter were located in the AWS US East 1 region, a factor to consider when interpreting the results. After the test, I recorded a latency of approximately 43ms for the URL shortening app, compared to a pre-test latency of around 9ms.

#### 2. <ins>Addressing Latency Concerns</ins>

The observed latency during the load test raised concerns about the application's ability to handle increased user traffic effectively. To mitigate this latency and improve the URL shortening application's performance, I recommended implementing a Content Delivery Network (CDN). CDNs enhance performance by reducing latency to web applications through the distribution and caching of static and certain dynamic content on geographically distributed edge servers (data centers). I selected [AWS CloudFront] as the CDN solution for the URL shortening app, due to seamless integration with AWS Elastic Beanstalk, which simplified configuration and management. After configuration, AWS CloudFront provided a new URL for accessing the application, offering low-latency access to cached content. I then conducted another Apache JMeter load test, using the same parameters, against the new URL for the application. The latency for the URL shortening app, while utilizing AWS CloudFront, measured at approximately 9.63ms under the test load.

#### 3. <ins>Primary Objective</ins>

The primary objective of this load testing scenario was to evaluate the performance of the Python URL Shortening application when exposed to a heavy request load. I initiated the process by establishing a baseline metric for the application's latency and subsequently subjecting it to stress testing. The insights gained from this testing informed our decision to enhance the application's infrastructure by introducing additional resources in the form of a CDN.
