---
id: dlkwo4jwjy3jnqgb7ymoeg4
title: In Middle of Partition Key with Start Sort Key
desc: ''
updated: 1684255486387
created: 1684255145479
---

<details>
<summary>Query with start sort key Java SDK 2.x</summary>


```java

package aws.ddb.snippets;

import java.util.HashMap;
import java.util.Map;

import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.services.dynamodb.DynamoDbClient;
import software.amazon.awssdk.services.dynamodb.model.AttributeValue;
import software.amazon.awssdk.services.dynamodb.model.QueryRequest;
import software.amazon.awssdk.services.dynamodb.model.QueryResponse;

public class QueryWithStartSortKey {

    private static final String TABLE_NAME = Constants.HashKeyRangeKeyTable.TABLE_NAME;
    private static final DynamoDbClient DDB = DynamoDbClient.builder()
        .region(Region.US_WEST_2)
        .build();

    public static void main(String[] args) {
        queryItems();
    }

    private static void queryItems() {
        final Map<String, AttributeValue> expressionAttributeValues = new HashMap<>();
        expressionAttributeValues.put(":v1", AttributeValue.builder().s("alphabet_200KB_per_row").build());
        expressionAttributeValues.put(":v2", AttributeValue.builder().s("70").build()); // ASCII value for 'F'

        final QueryRequest queryRequest = QueryRequest.builder()
            .tableName(TABLE_NAME)
            .keyConditionExpression("hash_key = :v1 and sort_key >= :v2")
            .expressionAttributeValues(expressionAttributeValues)
            .scanIndexForward(true)
            .build();

        final QueryResponse queryResponse = DDB.query(queryRequest);

        AlphabetOutUtil.printAll(queryResponse);
    }
}
```

Output:
```txt
sort_key: 70, letter: F, value: FFFFFFFFFF... value length=(204800)
sort_key: 71, letter: G, value: GGGGGGGGGG... value length=(204800)
sort_key: 72, letter: H, value: HHHHHHHHHH... value length=(204800)
sort_key: 73, letter: I, value: IIIIIIIIII... value length=(204800)
sort_key: 74, letter: J, value: JJJJJJJJJJ... value length=(204800)
sort_key: 75, letter: K, value: KKKKKKKKKK... value length=(204800)
```

GT Snapshot:
```bash
gt.sandbox.checkout.commit 355b0e2 \
&& cd "${GT_SANDBOX_REPO}/javaSandbox"
```

</details>
