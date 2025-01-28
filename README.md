# Unexpected behavior of $inc operator with string argument in MongoDB update query
This example demonstrates an uncommon error in MongoDB update queries where the `$inc` operator is used with a string argument instead of a number. This results in an unexpected behavior, and the `count` field may not be incremented correctly.

## Bug
The following query attempts to increment the `count` field by 1:
```javascript
db.collection('myCollection').updateOne({ _id: 1 }, { $inc: { count: '1' } });
```

However, because '1' is a string, the behavior is undefined and may lead to unexpected results.

## Solution
The correct way to increment the `count` field is to use a number:
```javascript
db.collection('myCollection').updateOne({ _id: 1 }, { $inc: { count: 1 } });
```