# Eventの値の処理

## Python 2.7

```python
# -*- coding: utf-8 -*-

import boto3

DYNAMO_TABLE = "TEST_TABLE"

def save_data(data):
    dynamodb = boto3.resource('dynamodb')
    table = dynamodb.Table(DYNAMO_TABLE)
    
    try:
        table.put_item(
            Item={
                "message": data,
            }
        )
        return "1"
    except Exception, e:
        error_code = e.response['Error']['Code']
        if error_code == "AccessDeniedException":
            print "DynamoDBにアクセスできない"
        return "-1"
        

def lambda_handler(event, context):
    result = save_data("Put Test")
    return result
```
|Error Coce|意味|
|:--|:--|
|AccessDeniedException|DynamoDBにアクセスできない|


```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents"
            ],
            "Resource": "arn:aws:logs:*:*:*"
        },
        {
            "Effect": "Allow",
            "Action": "dynamodb:*",
            "Resource": "*"
        }
    ]
}
```