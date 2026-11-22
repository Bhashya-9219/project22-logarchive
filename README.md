# Project 22: S3 Log Archive with Lifecycle

## Goal
Reduce storage costs by automatically expiring old log files from Amazon S3.

## AWS Resources
- S3 Bucket: mbproject22-log-archive-2026-590507089733-ap-south-1-an
- AWS Region: ap-south-1

## Implementation
1. Created an S3 bucket.
2. Created a sample application.log file.
3. Uploaded the log file to S3 under the logs/ prefix.
4. Configured an S3 lifecycle rule.
5. Enabled automatic expiration after 30 days.

## Lifecycle Configuration
- Rule Name: expire-old-logs
- Status: Enabled
- Prefix: logs/
- Expiration: 30 days

## Commands Used
```bash
aws s3 cp application.log s3://mbproject22-log-archive-2026-590507089733-ap-south-1-an/logs/application.log

aws s3api put-bucket-lifecycle-configuration \
  --bucket mbproject22-log-archive-2026-590507089733-ap-south-1-an \
  --lifecycle-configuration file://lifecycle.json

aws s3api get-bucket-lifecycle-configuration \
  --bucket mbproject22-log-archive-2026-590507089733-ap-south-1-an
```

## Result
Successfully uploaded logs to Amazon S3 and configured an enabled 30-day lifecycle expiration rule.
