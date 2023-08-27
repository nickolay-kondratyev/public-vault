---
id: lpxdgmtcmiok8y8lm1ynb0d
title: create-hashKey-table
desc: ''
updated: 1686613194628
created: 1686612730099
---

```java
package aws.ddb.snippets;

import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.services.dynamodb.DynamoDbClient;
import software.amazon.awssdk.services.dynamodb.model.*;

public class CreateHashKeyTable {

    public static final String TABLE_NAME = "PrimaryKeyOnlyTable";

    public static void main(String[] args) {

        final DynamoDbClient ddb = DynamoDbClient.builder()
            .region(Region.US_WEST_2)
            .build();

        try {
            System.out.println("Attempting to create table; please wait...");
            CreateTableRequest request = CreateTableRequest.builder()
                .attributeDefinitions(AttributeDefinition.builder()
                    .attributeName("pk")
                    .attributeType(ScalarAttributeType.S)
                    .build())
                .keySchema(KeySchemaElement.builder()
                    .attributeName("pk")
                    .keyType(KeyType.HASH)
                    .build())
                .billingMode(BillingMode.PAY_PER_REQUEST)
                .tableName(TABLE_NAME)
                .build();

            final CreateTableResponse response = ddb.createTable(request);
            System.out.println("response: " + response.tableDescription().tableName());
            System.out.println("Table is being created...");

        } catch (DynamoDbException e) {
            System.err.println("Unable to create table: ");
            System.err.println(e.awsErrorDetails().errorMessage());
        }
    }
}
```


```bash
gt.sandbox.checkout.commit f5126db \
&& cd "${GT_SANDBOX_REPO}"
```
