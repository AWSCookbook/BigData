# Streaming Data to Amazon S3 Using Amazon Kinesis Data Firehose
### Preparation
Preparation
### Set a unique suffix to use for the S3 bucket name:
```
RANDOM_STRING=$(aws secretsmanager get-random-password \
--exclude-punctuation --exclude-uppercase \
--password-length 6 --require-each-included-type \
--output text \
--query RandomPassword)
```

### Create a S3 bucket for data:
```
aws s3api create-bucket --bucket awscookbook702-$RANDOM_STRING
```

### Create a Kinesis stream:
```
aws kinesis create-stream --stream-name AWSCookbook702 --shard-count 1
```

### Confirm that your stream is in ACTIVE state:
```
aws kinesis describe-stream-summary --stream-name AWSCookbook702
```

## Clean up 

```
You can delete the Kinesis Delivery Stream and Kinesis Stream from within the Kinesis console. Click the Delivery streams link in the left navigation menu, choose the stream you created, and click the Delete delivery stream button. Click the Data streams link and choose your data stream, then click the Delete stream button.

Empty the S3 bucket that you created and delete the bucket using the S3 console. You can click the “Empty” button and then the Delete button to accomplish this.

```

### Delete the Kinesis Stream:
`aws kinesis delete-stream --stream-name AWSCookbook702`

### Clean up the local variable you created:

