## cloudfront {#cloudfront}

* delivery
 
  * request-ROUTE53-edge location-Origin server
  * supports both static and dynamic content
* RMTP
 
  * S3 bucket as the origin
  * users view media files using the media player that is provided by cloudfront; not the locally installed
  * Web distribution for media Player and RMTP distribution for media files
* private content
 
  * OAI Origin Access Identity
  * add header in http server, Origin to verify the request has come from CloudFront
* feature
 
  * signed URLs and signed cookies
 
    * for RTMP distribution
    * restrict access to individual files
    * access to multiple restricted files
  * Caching Based on Request Headers
  * Geo Restriction
  * Compressed Files
 
    * Content-Encoding header on the file must not be gzip
    * viewer uncompresses the file
  * multi-upload to S3
* SNI
 
  * Server Name Indication， 同一个IP可用选择多个hostname, 用自己的SSL证书时选择，一般是客户端浏览器的选项
* Dedicated IP
 
  * 专属主机IP，不和其他hostname共用，传统SSL使用，现在大部分用SNI
* https with S3, s3不能独立用https， 但是结合cloudfront, 用 ACM Amazon Certificate Manager 生成的证书可以通讯
* price
 
  * charge with: data out, request, Invalidation request, SSL certificates



