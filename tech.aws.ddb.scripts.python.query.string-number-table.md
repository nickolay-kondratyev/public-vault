---
id: h0lv9qbn3sdts89n2r1u4wu
title: String Number Table
desc: ''
updated: 1691447108659
created: 1691420442905
---

```py
import boto3

# Initialize the DynamoDB client
dynamodb = boto3.resource('dynamodb')

# Define the table name and primary/range key names
TABLE_NAME = 'YourTableName'
PRIMARY_KEY_NAME = 'YourPrimaryKeyName'
RANGE_KEY_NAME = 'YourRangeKeyName'

def query_table(primary_key_value, range_key_value):
    """
    Query the DynamoDB table based on primary and range key values.

    Args:
    - primary_key_value (str): The value of the primary key to query.
    - range_key_value (int): The value of the range key to query.

    Returns:
    - list: A list of items that match the query.
    """
    table = dynamodb.Table(TABLE_NAME)

    response = table.query(
        KeyConditionExpression=boto3.dynamodb.conditions.Key(PRIMARY_KEY_NAME).eq(primary_key_value) & 
                               boto3.dynamodb.conditions.Key(RANGE_KEY_NAME).eq(range_key_value)
    )

    return response['Items']

# Example usage
if __name__ == "__main__":
    primary_key_value = "YourPrimaryKeyValue"
    range_key_value = 12345  # Replace with your range key value

    items = query_table(primary_key_value, range_key_value)
    for item in items:
        print(item)


```
