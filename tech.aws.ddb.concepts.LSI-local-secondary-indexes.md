---
id: m83yqy7sv8cqih7d9gtzc49
title: LSI-local-secondary-indexes
desc: ''
updated: 1684256192335
created: 1684253444268
---

> A local secondary index maintains an alternate sort key for a given partition key value. [aws](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/LSI.html)


<details>
<summary>Explain like I am 5 years old.</summary>

Alright kiddo, let's imagine you have a big box of Legos. Each Lego brick is different - they have different colors, sizes, and shapes.

Now, let's say you want to play with only the red Lego bricks. What you could do is go through the entire box each time you want a red brick, but that would take a lot of time, right? Instead, you could sort out all the red Lego bricks into their own smaller box. Then, whenever you want a red brick, you just go to that smaller box, and voila, you've got your red Legos all ready to play with!

In the world of databases, like DynamoDB, this smaller box is like a "Local Secondary Index" (LSI). In DynamoDB, each piece of data, or 'item', is like a Lego brick. An item has something called a 'partition key' and a 'sort key'. Think of the partition key as the main color of the Lego, and the sort key as the size of the Lego.

But what if you wanted to quickly find all your Legos not just by color, but by size? Here's where the LSI comes in. An LSI allows you to sort your data (or 'Legos') by a different 'sort key' within each partition key (or 'color'). So, if you had an LSI on size, you could easily find all your small red Legos or large red Legos, without having to look through the whole box.

Remember, though, LSIs only work within each color (or partition key). So if you're looking for small Legos, you'd need to look in each color's box, one by one. But it still makes finding your Legos a whole lot faster!

That's how Local Secondary Indexes work in DynamoDB. They help us find and use the data we want more quickly, just like sorting your Lego bricks into smaller boxes helps you play more efficiently. #chatgpt4

</details>

<details>
<summary>Can only create LSI at table creation time</summary>

> You specify which attributes are projected into the local secondary index when you create the table. - [aws doc](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/LSI.html)

According to the DynamoDB documentation and [stackoverflow](https://stackoverflow.com/questions/36493323/adding-new-local-secondary-index-to-an-existing-dynamodb-table), local secondary indexes in DynamoDB can only be created at the same time as the table is created. It is not possible to add a local secondary index to an existing table. However, it is possible to add a global secondary index to an existing table. #phind
</details>
