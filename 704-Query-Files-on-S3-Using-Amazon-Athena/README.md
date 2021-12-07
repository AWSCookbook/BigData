# Query Files on S3 Using Amazon Athena
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
aws s3api create-bucket --bucket awscookbook704-$RANDOM_STRING
```

### Create S3 prefixes for results and data:
```
aws s3 mb s3://awscookbook704-$RANDOM_STRING/results/
aws s3 mb s3://awscookbook704-$RANDOM_STRING/data/
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
aws s3 cp titles.csv s3://awscookbook704-$RANDOM_STRING/data/
```

## Clean up 

```
Open the Query Editor and run the following two SQL statements:

DROP TABLE `awscookbook704table`;

DROP DATABASE `awscookbook704db`;

Delete the contents of the S3 bucket you created and delete the bucket. The S3 Console provides an easy way to empty the bucket with the “Empty” button.

```
