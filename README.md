# spring-boot-dynamodb
## Getting Started
### DynamoDB local
```
docker run -p 8000:8000 amazon/dynamodb-local
```
### AWS configuration
Make sure Amazon AWS env variables are set:
- AWS_ACCESS_KEY_ID
- AWS_SECRET_KEY
## Swagger UI
http://localhost:8080/swagger-ui.html
## Documentation
- [Official AWS DynamoDB Documentation](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GettingStarted.Java.html)
- [Community Spring Module for data access on AWS DynamoDB](https://github.com/derjust/spring-data-dynamodb)
- [Example using the Spring module](https://www.baeldung.com/spring-data-dynamodb)

---
# # DynamoDB on localhost (Docker)

[example](https://dzone.com/articles/getting-started-with-dynamodb-and-spring)
[git](https://github.com/smartinrub/spring-boot-dynamodb)

## ## Install
[source](https://medium.com/devopslinks/dynamodb-on-localhost-9c502f07056e)

## ## Config
[source](https://github.com/ruanbekker/dynamodb-local-docker/blob/master/README.md)

```shell
pip install awscli
```

```shell
aws configure
```

## ## Docker

```shell
docker pull amazon/dynamodb-local
```

```shell
docker run -p 8000:8000 amazon/dynamodb-local
```

```shell
docker run -it --rm -v d:/Root/MyPrograms/Java/zprime-service/target:/home/dynamodblocal/data -p 8000:8000 amazon/dynamodb-local -Djava.library.path=./DynamoDBLocal_lib -jar DynamoDBLocal.jar -sharedDb -dbPath ./data
```

## ## Get all items from table

```shell
aws dynamodb scan --table-name Hotels --endpoint-url http://localhost:8000
```

## ## Issue: credentials were not defined
Issue:
Unable to create table: Unable to load AWS credentials from any provider in the chain: 
[EnvironmentVariableCredentialsProvider: 
Unable to load AWS credentials from environment variables (AWS_ACCESS_KEY_ID (or AWS_ACCESS_KEY) and AWS_SECRET_KEY (or AWS_SECRET_ACCESS_KEY)), 
SystemPropertiesCredentialsProvider: Unable to load AWS credentials from Java system properties (aws.accessKeyId and aws.secretKey), 
com.amazonaws.auth.profile.ProfileCredentialsProvider@21457192: profile file cannot be null, com.amazonaws.auth.EC2ContainerCredentialsProviderWrapper@be67096: Unable to load credentials from service endpoint]

Resolution:
Should be defined by `aws-cli` (see Config section here)