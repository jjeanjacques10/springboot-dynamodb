# Spring Boot + DynamoDb

Project example of how to implement AWS DynamoDb in Spring Boot

## Technologies

* Java 11
* Spring Boot
* DynamoDb

## Database Config

You must set your credentials from AWS in the [DynamoDbConfiguration](/src/main/java/com/jjeanjacques/DynamoDbSpringBoot/config/DynamoDbConfiguration.java) file

``` java
private AmazonDynamoDB buildAmazonDynamoDb() {
    return AmazonDynamoDBClientBuilder
            .standard()
            .withEndpointConfiguration(
                    new AwsClientBuilder.EndpointConfiguration(
                            "dynamodb.{{YOUR-REGION}}.amazonaws.com",
                            "{{YOUR-REGION}}"
                    )
            ).withCredentials(
                    new AWSStaticCredentialsProvider(
                            new BasicAWSCredentials(
                                    "{{YOUR-ACCESS-KEY}}",
                                    "{{YOUR-SECRET-KEY}}"
                            )
                    )
            ).build();
}
```

## Collection Example

You can access the postman collection [here](/postman/Examples%20-%20AWS%20DynamoDb%20-%20Spring%20Boot.postman_collection.json)

### Employees
- **GET** - /employee/{id} 

Get dynamoDb filtering employee by Id
  
- **POST** - /employee

Create employee in dynamoDb

``` json
{
    "firstName": "Jean",
    "lastName": "Barros",
    "email": "jjean.jacques10@gmail.com",
    "department": {
        "departmentName": "IT",
        "departmentCode": "IT--006"
    }
}
```

- **PUT** - /employee/{id}

Update employee in dynamoDb 

``` json
{
    "firstName": "Jean",
    "lastName": "Jacques",
    "email": "jean2@gmail.com",
    "department": {
        "departmentName": "IT",
        "departmentCode": "IT--010"
    }
}
```

- **DELETE** - /employee/{id}

Delete employee in dynamoDb

---
Developed by [Jean Jacques](https://github.com/jjeanjacques10/)