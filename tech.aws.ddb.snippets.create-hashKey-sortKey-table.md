---
id: w6nsgdmafnexihjhsodik2x
title: create-hashKey-sortKey DDB table
desc: ''
updated: 1684203717256
created: 1684202791394
---

<details>
<summary>Code snippet java 2.x SDK</summary>

```java
package aws.ddb.snippets;

import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.services.dynamodb.DynamoDbClient;
import software.amazon.awssdk.services.dynamodb.model.*;

    public class DynamoDBCreateTable {

    public static void main(String[] args) {

        final DynamoDbClient ddb = DynamoDbClient.builder()
            .region(Region.US_WEST_2)
            .build();

        final CreateTableRequest request = CreateTableRequest.builder()
            .attributeDefinitions(
                AttributeDefinition.builder()
                    .attributeName(Constants.HashKeyRangeKeyTable.HASH_KEY)
                    .attributeType(ScalarAttributeType.S)
                    .build(),
                AttributeDefinition.builder()
                    .attributeName(Constants.HashKeyRangeKeyTable.SORT_KEY)
                    .attributeType(ScalarAttributeType.S)
                    .build())
            .keySchema(
                KeySchemaElement.builder()
                    .attributeName(Constants.HashKeyRangeKeyTable.HASH_KEY)
                    .keyType(KeyType.HASH)
                    .build(),
                KeySchemaElement.builder()
                    .attributeName(Constants.HashKeyRangeKeyTable.SORT_KEY)
                    .keyType(KeyType.RANGE)
                    .build())
            .tableName(Constants.HashKeyRangeKeyTable.TABLE_NAME)
            .billingMode(BillingMode.PAY_PER_REQUEST)
            .build();

        final CreateTableResponse response = ddb.createTable(request);
        System.out.println("Successful create response for table: " + response.tableDescription().tableName());
        System.out.println("Note running this will fail since the table already excists.");
    }
}
```
</details>

<details>
<summary>GT commit</summary>

```bash
gt.sandbox.checkout.commit ce47683 \
&& cd "${GT_SANDBOX_REPO}/javaSandbox"
```
</details>


