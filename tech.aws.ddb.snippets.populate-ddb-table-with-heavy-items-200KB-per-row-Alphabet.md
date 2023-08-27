---
id: zk2xf5ldaqe6dtr6rys6082
title: populate-ddb-table-with-heavy-items-200KB-per-row-Alphabet
desc: ''
updated: 1684255394532
created: 1684204562114
---

Populates the table with 
- hashKey: alphabet_200KB_per_row
- SortKey: ASCII number of upper case letter.

<details>
<summary>Code snippet java 2.x SDK</summary>

```java

package aws.ddb.snippets;

import java.util.HashMap;
import java.util.Map;
import java.util.stream.IntStream;

import software.amazon.awssdk.services.dynamodb.DynamoDbClient;
import software.amazon.awssdk.services.dynamodb.model.AttributeValue;
import software.amazon.awssdk.services.dynamodb.model.PutItemRequest;

public class PopulateDynamoDBTableWith200KB_PerRow {


    public static void main(String[] args) {
        final DynamoDbClient ddb = Factory.getClient();

        final char[] alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".toCharArray();

        // Generate a 200KB string for each letter
        for (final char letter : alphabet) {
            // repeat letter to create a 200KB string
            final String value = repeatChar(letter, 200 * 1024);

            final Map<String, AttributeValue> item = new HashMap<>();
            item.put("hash_key", AttributeValue.builder().s("alphabet_200KB_per_row").build());
            item.put("sort_key", AttributeValue.builder().s(String.valueOf((int) letter)).build());
            item.put("letter", AttributeValue.builder().s(String.valueOf(letter)).build());
            item.put("value", AttributeValue.builder().s(value).build());

            final PutItemRequest request = PutItemRequest.builder()
                .tableName(Constants.HashKeyRangeKeyTable.TABLE_NAME)
                .item(item)
                .build();

            ddb.putItem(request);

            System.out.println("Put item for letter: " + letter);
        }
    }

    private static String repeatChar(char c, int size) {
        StringBuilder sb = new StringBuilder(size);
        IntStream.range(0, size).forEach(i -> sb.append(c));
        return sb.toString();
    }
}
```

```bash
gt.sandbox.checkout.commit 5a4c107 \
&& cd "${GT_SANDBOX_REPO}/javaSandbox"
```
</details>


<details>
<summary>Code with GUID added on in sort key java 2.x </summary>

```java
package aws.ddb.snippets;

import java.util.HashMap;
import java.util.Map;
import java.util.UUID;
import java.util.stream.IntStream;

import software.amazon.awssdk.services.dynamodb.DynamoDbClient;
import software.amazon.awssdk.services.dynamodb.model.AttributeValue;
import software.amazon.awssdk.services.dynamodb.model.PutItemRequest;

public class PopulateDynamoDBTableWith200KB_PerRow {


    public static void main(String[] args) {

        final DynamoDbClient ddb = Factory.getClient();

        final char[] alphabet = getUppercaseAlphabet();

        // Generate a 200KB string for each letter
        for (final char letter : alphabet) {
            // repeat letter to create a 200KB string
            final String value = repeatChar(letter, 200 * 1024);

            final Map<String, AttributeValue> item = new HashMap<>();
            item.put("hash_key", AttributeValue.builder().s("alphabet_200KB_per_row_with_GUID_in_SortKey").build());
            final String sortKey = (int) letter + "__" + UUID.randomUUID();
            item.put("sort_key", AttributeValue.builder().s(sortKey).build());
            item.put("letter", AttributeValue.builder().s(String.valueOf(letter)).build());
            item.put("value", AttributeValue.builder().s(value).build());

            final PutItemRequest request = PutItemRequest.builder()
                .tableName(Constants.HashKeyRangeKeyTable.TABLE_NAME)
                .item(item)
                .build();

            ddb.putItem(request);

            System.out.println("Put item for letter: " + letter);
        }
    }

    private static char[] getUppercaseAlphabet() {

        return "ABCDEFGHIJKLMNOPQRSTUVWXYZ".toCharArray();
    }

    private static String repeatChar(char c, int size) {

        StringBuilder sb = new StringBuilder(size);
        IntStream.range(0, size).forEach(i -> sb.append(c));
        return sb.toString();
    }
}
```

```bash
gt.sandbox.checkout.commit 625e5af \
&& cd "${GT_SANDBOX_REPO}/javaSandbox"
```
</details>


## Related
- To create this table refer to [[tech.aws.ddb.snippets.create-hashKey-sortKey-table]]
- To query this table refer to [[tech.aws.ddb.snippets.query.in-ascending-descending-order]]