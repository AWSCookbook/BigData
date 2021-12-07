# Automatically Discover Metadata with AWS Glue Crawlers
## Preparation
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
aws s3api create-bucket --bucket awscookbook703-$RANDOM_STRING
```

### Create S3 prefixes for results and data:
```
aws s3 mb s3://awscookbook703-$RANDOM_STRING/results/
aws s3 mb s3://awscookbook703-$RANDOM_STRING/data/
```

### Download a public dataset
```
curl -vk https://www.bl.uk/bibliographic/downloads/ComicsResearcherFormat_202104_csv.zip -O ComicsResearcherFormat_202104_csv.zip
```

### Unzip the dataset
```
unzip ComicsResearcherFormat_202104_csv.zip
```

### Copy the titles.csv file to your S3 bucket
```
aws s3 cp titles.csv s3://awscookbook703-$RANDOM_STRING/data/
```

## Clean up 

### Delete the Crawler:
`Select the crawler from the AWS Glue Console, select Actions, and choose Delete.`

### Empty the S3 bucket you created in the preparation steps and delete the bucket
`Empty the S3 bucket you created in the preparation steps and delete the bucket`
