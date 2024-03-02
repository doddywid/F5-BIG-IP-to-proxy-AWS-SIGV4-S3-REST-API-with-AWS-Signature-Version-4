This repository explains the mechanism to expose (a.k.a proxy) AWS S3 Bucket using REST API through F5 BIG-IP.
As per this writing date, latest AWS authorization for REST API requests is using AWS Signature Version 4 (will be shortened as SIGV4 througout the rest of this repo).

This is sometimes required when you are dealing with situation where you need to access your S3 objects from outside AWS environment, and have limitation (or not willing) to use AWS cli/SDK.
The diagram can be seen as below
