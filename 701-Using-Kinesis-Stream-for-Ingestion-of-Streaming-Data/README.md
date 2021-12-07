# Using a Kinesis Stream for Ingestion of Streaming Data


## Clean up 

### Delete the Kinesis Stream:
`aws kinesis delete-stream --stream-name AWSCookbook701`

### Clean up the local variable you created:
`unset SHARD_ITERATOR`
