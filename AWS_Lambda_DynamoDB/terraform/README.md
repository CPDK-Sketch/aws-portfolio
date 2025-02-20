## AWS Lambda with DynamoDB

## Overview
This project demonstrates how to create an AWS Lambda function that interacts with DynamoDB to store user data.

### AWS Services Used:
- **Lambda**: Serverless compute service to run code.
- **DynamoDB**: NoSQL database to store user data.
- **API Gateway**: Expose a RESTful API to trigger the Lambda function.

### Steps:
1. **Create a DynamoDB table** (`UserTable`).
2. **Create a Lambda function** to insert data into DynamoDB.
3. **Set up API Gateway** to trigger the Lambda function.

### Code (Python Lambda Example):
```python
import json
import boto3
from datetime import datetime

dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('UserTable')

def lambda_handler(event, context):
    user_data = event['body']
    user_id = user_data.get('userID')
    name = user_data.get('name')
    timestamp = str(datetime.utcnow())

    response = table.put_item(
        Item={
            'userID': user_id,
            'timestamp': timestamp,
            'name': name
        }
    )

    return {
        'statusCode': 200,
        'body': json.dumps('Data inserted successfully!')
    }
