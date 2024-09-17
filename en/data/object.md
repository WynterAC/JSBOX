# Object

Here's a table shows all types handled by iOS automatically:

  Objective-C type  |   JavaScript type
--------------------|---------------------
        nil         |     undefined
      NSNull        |        null
      NSString      |       string
      NSNumber      |   number, boolean
    NSDictionary    |   Object object
      NSArray       |    Array object
      NSDate        |     Date object
      NSBlock (1)   |   Function object (1)
        id (2)      |   Wrapper object (2)
      Class (3)     | Constructor object (3)

But if we get an object from iOS native interface, it's not easy to know its properties.

For example:

```js
didSelect: function(tableView, indexPath) {
  var row = indexPath.row
}
```

`indexPath` is actually an native object, in this example we can access its properties with `.section` and `.row`.

To understand iOS native objects, we provided a table: [Object Properties](en/object/data.md).

# $props

`$props` helps you get all properties of an object:

```js
const props = $props("string");
```

$props is just a simple JavaScript function, it implemented like:

```js
const $props = object => {
  const result = [];
  for (; object != null; object = Object.getPrototypeOf(object)) {
    const names = Object.getOwnPropertyNames(object);
    for (let idx=0; idx<names.length; idx++) {
      const name = names[idx];
      if (!result.includes(name)) {
        result.push(name)
      }
    }
  }
  return result
};
```

# $desc

`$desc` returns description of an object:

```js
let desc = $desc(object);
console.log(desc);
```