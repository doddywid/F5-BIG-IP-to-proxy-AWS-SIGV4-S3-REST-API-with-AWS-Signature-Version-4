# **F5 BIG-IP as Proxy for AWS S3 REST API with AWS Signature Version 4 (SIGV4)**

This repository provide the mechanism to expose (a.k.a proxying) AWS S3 Bucket using REST API through F5 BIG-IP.
As per the writing date, latest AWS authorization for REST API requests is using AWS Signature Version 4 (will be shortened as SIGV4 througout the rest of this repo).

This is sometimes required when you are dealing with situation where you need to access your S3 objects from outside AWS environment, and have limitation (or not willing) to use AWS cli/SDK.

The diagram can be seen as below

![alt text](https://github.com/doddywid/F5-BIG-IP-to-proxy-AWS-SIGV4-S3-REST-API-with-AWS-Signature-Version-4/blob/main/topology.png)

File structure:
- ltm_datagroup: ltm datagroup configuration, for storing fixed variables like api access key, api secret, region, service, algorithm, etc.
- server-ssl-profile: configuration for server-side SSL profile. SNI in this profile needs to match S3 API endpoint host
- irule_s3_proxy_v2.2: iRule for cryptographic tasks & calculating SIGV4 authorization header
- irule_s3_proxy_v2.1: previous version of iRule for cryptographic tasks & calculating SIGV4 authorization header. This version does not include payload in signing process
- virtual-server: ltm virtual server configuration.
