### Cloud Watch Metrics

* Elastic Load Balancing publishes data points to Amazon CloudWatch about your load balancers and back-end instances
* Elastic Load Balancing reports metrics to CloudWatch only when requests are flowing through the load balancer. If there are requests flowing through the load balancer, Elastic Load Balancing measures and sends its metrics in 60-second intervals. If there are no requests flowing through the load balancer or no data for a metric, the metric is not reported.

Following metrics are available

* **HealthyHostCount, UnHealthyHostCount**
  * Number of healthy and unhealthy instances registered with the load balancer.
  * Most useful statistics are average, min, and max
* **RequestCount**
  * Number of requests completed or connections made during the specified interval \(1 or 5 minutes\).
  * Most useful statistic is sum
* **Latency**
  * Time elapsed, in seconds, after the request leaves the load balancer until the headers of the response are received.
  * Most useful statistic is average
* **SurgeQueueLength**
  * Total number of requests that are pending routing.
  * Load balancer queues a request if it is unable to establish a connection with a healthy instance in order to route the request.
  * Maximum size of the queue is 1,024. Additional requests are rejected when the queue is full.
  * Most useful statistic is max, because it represents the peak of queued requests.
* **SpilloverCount**
  * The total number of requests that were rejected because the surge queue is full. Should ideally be 0
  * Most useful statistic is sum.
* **HTTPCode\_ELB\_4XX, HTTPCode\_ELB\_5XX**
  * Client and Server error code generated by the load balancer
  * Most useful statistic is sum.
* **HTTPCode\_Backend\_2XX, HTTPCode\_Backend\_3XX, HTTPCode\_Backend\_4XX, HTTPCode\_Backend\_5XX**
  * Number of HTTP response codes generated by registered instances
  * Most useful statistic is sum.

### Elastic Load Balancer access logs

* Elastic Load Balancing provides access logs that capture detailed information about all requests sent to your load balancer.
* Each log contains information such as the time the request was received, the client’s IP address, latencies, request paths, and server responses.
* Elastic Load Balancing captures the logs and stores them in the Amazon S3 bucket
* Access logging is disabled by default and can be enabled without any additional charge. You are only charged for S3 storage

### CloudTrail Logs

* AWS CloudTrail can be used to capture all calls to the Elastic Load Balancing API made by or on behalf of your AWS account and either made using Elastic Load Balancing API directly, or indirectly through the AWS Management Console or AWS CLI
* CloudTrail stores the information as log files in an Amazon S3 bucket that you specify.
* Logs collected by CloudTrail can be used to monitor the activity of your load balancers and determine what API call was made, what source IP address was used, who made the call, when it was made, and so on



