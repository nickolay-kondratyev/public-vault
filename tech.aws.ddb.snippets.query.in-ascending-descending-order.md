---
id: 2ihmolm82rgxsu1aejecwr7
title: In Ascending Descending Order
desc: ''
updated: 1684254849286
created: 1684205348034
---

<details>
<summary>Code snippet 2.x SDK, java</summary>

```java

package aws.ddb.snippets;

import java.util.HashMap;
import java.util.Map;
import javax.swing.*;

import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.services.dynamodb.DynamoDbClient;
import software.amazon.awssdk.services.dynamodb.model.AttributeValue;
import software.amazon.awssdk.services.dynamodb.model.QueryRequest;
import software.amazon.awssdk.services.dynamodb.model.QueryResponse;

public class DynamoDBQueryTable {

    private static final String TABLE_NAME = Constants.HashKeyRangeKeyTable.TABLE_NAME;
    private static final String HASH_KEY_VALUE = "alphabet_200KB_per_row";
    private static final DynamoDbClient ddb;

    static {
        ddb = software.amazon.awssdk.services.dynamodb.DynamoDbClient.builder()
            .region(Region.US_WEST_2)
            .build();
    }

    public static void main(String[] args) {

        queryTableInOrder(SortOrder.ASCENDING);
        queryTableInOrder(SortOrder.DESCENDING);
    }

    private static void queryTableInOrder(final SortOrder sortOrder) {

        System.out.println("--------------------------------------------------------------------------------");
        System.out.println("Querying in " + sortOrder + " order of sort_key");

        final Map<String, AttributeValue> expressionAttributeValues = new HashMap<>();
        expressionAttributeValues.put(":v1", AttributeValue.builder().s(HASH_KEY_VALUE).build());

        final QueryRequest queryRequest = QueryRequest.builder()
            .tableName(TABLE_NAME)
            .keyConditionExpression("hash_key = :v1")
            .expressionAttributeValues(expressionAttributeValues)
            .scanIndexForward(sortOrder == SortOrder.ASCENDING)
            .build();

        final QueryResponse queryResponse = ddb.query(queryRequest);

        queryResponse.items().forEach(item -> {
            System.out.println(
                "sort_key: " + item.get("sort_key").s() +
                ", letter: " + item.get("letter").s() +
                ", value: " + item.get("value").s().substring(0, 10) +
                "... value length=(" + item.get("value").s().length() + ")");
        });
    }
}
```

GT commit: 
```bash
gt.sandbox.checkout.commit 9d6c910 \
&& cd "${GT_SANDBOX_REPO}/javaSandbox"
```

Output:
```txt
Querying in ASCENDING order of sort_key
sort_key: 65, letter: A, value: AAAAAAAAAA... value length=(204800)
sort_key: 66, letter: B, value: BBBBBBBBBB... value length=(204800)
sort_key: 67, letter: C, value: CCCCCCCCCC... value length=(204800)
sort_key: 68, letter: D, value: DDDDDDDDDD... value length=(204800)
sort_key: 69, letter: E, value: EEEEEEEEEE... value length=(204800)
sort_key: 70, letter: F, value: FFFFFFFFFF... value length=(204800)
--------------------------------------------------------------------------------
Querying in DESCENDING order of sort_key
sort_key: 90, letter: Z, value: ZZZZZZZZZZ... value length=(204800)
sort_key: 89, letter: Y, value: YYYYYYYYYY... value length=(204800)
sort_key: 88, letter: X, value: XXXXXXXXXX... value length=(204800)
sort_key: 87, letter: W, value: WWWWWWWWWW... value length=(204800)
sort_key: 86, letter: V, value: VVVVVVVVVV... value length=(204800)
sort_key: 85, letter: U, value: UUUUUUUUUU... value length=(204800)
```

Related: [[aws.ddb.snippets.populate-ddb-table-with-heavy-items-200KB-per-row]]
</details>



