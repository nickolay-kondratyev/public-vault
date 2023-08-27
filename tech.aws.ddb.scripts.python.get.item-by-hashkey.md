---
id: ici42r1oclkiop9aiuaxhq4
title: Item by Hashkey
desc: ''
updated: 1691447134342
created: 1691447117743
---


GET ITEM single 

```py
import boto3

# Initialize the DynamoDB client
dynamodb = boto3.resource('dynamodb')

# Define the table name and primary key name
TABLE_NAME = 'YourTableName'
PRIMARY_KEY_NAME = 'YourPrimaryKeyName'

def get_item(primary_key_value):
    """
    Retrieve an item from the DynamoDB table based on the primary key value.

    Args:
    - primary_key_value (str): The value of the primary key to retrieve.

    Returns:
    - dict: The item that matches the primary key value, or None if not found.
    """
    table = dynamodb.Table(TABLE_NAME)

    response = table.get_item(
        Key={
            PRIMARY_KEY_NAME: primary_key_value
        }
    )

    return response.get('Item', None)

# Example usage
if __name__ == "__main__":
    primary_key_value = "YourPrimaryKeyValue"

    item = get_item(primary_key_value)
    if item:
        print(item)
    else:
        print(f"No item found with primary key value: {primary_key_value}")


```
