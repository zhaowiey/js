# JavaScript 字符串详解 13

标签（空格分隔）： JS

---

## 定义

字符串是由0个或者多个16位的Unicode编码组成的字符集合。

## 常用方法

**查找类**

### str.indexOf(searchValue[, fromIndex])

> 返回指定值的第一次出现的调用  String 对象中的索引，开始在fromIndex进行搜索。如果未找到该值，则返回-1。

- searchValue: 一个字符串表示被查找的值。
- fromIndex: 可选表示调用该方法的字符串中开始查找的位置。可以是任意整数。默认值为 0。如果 fromIndex < 0 则查找整个字符串（如同传进了 0）。如果 fromIndex >= str.length，则该方法返回 -1，除非被查找的字符串是一个空字符串，此时返回 str.length。

字符串中的字符被从左向右索引。首字符的索引（index）为 0，字符串 stringName 的最后一个字符的索引是 stringName.length - 1。

```
"Blue Whale".indexOf("Blue");     // returns  0
"Blue Whale".indexOf("Blute");    // returns -1
"Blue Whale".indexOf("Whale", 0); // returns  5
"Blue Whale".indexOf("Whale", 5); // returns  5
"Blue Whale".indexOf("", 9);      // returns  9
"Blue Whale".indexOf("", 10);     // returns 10
"Blue Whale".indexOf("", 11);     // returns 10
```

### str.lastIndexOf(searchValue[, fromIndex])

> 返回指定值在调用该方法的字符串中最后出现的位置，如果没找到则返回 -1。从该字符串的后面向前查找，从 fromIndex 处开始。

- searchValue: 一个字符串，表示被查找的值。
- fromIndex: 从调用该方法字符串的此位置处开始查找。可以是任意整数。默认值为 str.length。如果为负值，则被看作 0。如果 fromIndex > str.length，则 fromIndex 被看作 str.length。

字符串中的字符被从左向右索引。首字符的索引（index）是 0，最后一个字符的索引是 stringName.length - 1。

```
"canal".lastIndexOf("a")   // returns 3
"canal".lastIndexOf("a",2) // returns 1
"canal".lastIndexOf("a",0) // returns -1
"canal".lastIndexOf("x")   // returns -1
```


### str.includes(searchString[, position])

> includes() 方法用于判断一个字符串是否包含在另一个字符串中，根据情况返回true或false。

- searchString: 要在此字符串中搜索的字符串。
- position: 可选。从当前字符串的哪个索引位置开始搜寻子字符串；默认值为0。

```
var str = 'To be, or not to be, that is the question.';

console.log(str.includes('To be'));       // true
console.log(str.includes('question'));    // true
console.log(str.includes('nonexistent')); // false
console.log(str.includes('To be', 1));    // false
console.log(str.includes('TO BE'));       // false
```

### str.startsWith(searchString [, position])

> 用来判断当前字符串是否是以另外一个给定的子字符串“开头”的，根据判断结果返回 true 或 false。

- searchString: 要搜索的子字符串。
- position: 在 str 中搜索 searchString 的开始位置，默认值为 0，也就是真正的字符串开头处。

```
var str = "To be, or not to be, that is the question.";

alert(str.startsWith("To be"));         // true
alert(str.startsWith("not to be"));     // false
alert(str.startsWith("not to be", 10)); // true
```

### str.endsWith(searchString [, position])

用来判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 true 或 false。

- searchString: 要搜索的子字符串。
- position: 在 str 中搜索 searchString 的结束位置，默认值为 str.length，也就是真正的字符串结尾处。

```
var str = "To be, or not to be, that is the question.";

alert( str.endsWith("question.") );  // true
alert( str.endsWith("to be") );      // false
alert( str.endsWith("to be", 19) );  // true
alert( str.endsWith("To be", 5) );   // true
```

**截取类**

### str.substr(start[, length])

> 返回字符串中从指定位置开始到指定长度的子字符串。

- start: 开始提取字符的位置。如果为负值，则被看作 strLength + start，其中 strLength 为字符串的长度（例如，如果 start 为 -3，则被看作 strLength-3）。

- length: 可选。提取的字符数。

### str.substring(indexStart[, indexEnd])

> 返回字符串两个索引之间（或到字符串末尾）的子串。

- indexStart: 一个 0 到字符串长度之间的整数。
- indexEnd: 可选。一个 0 到字符串长度之间的整数。
start 是一个字符的索引。首字符的索引为 0，最后一个字符的索引为 字符串的长度减去1。substr 从 start 位置开始提取字符，提取 length 个字符（或直到字符串的末尾）。

如果 start 为正值，且大于或等于字符串的长度，则 substr 返回一个空字符串。

如果 start 为负值，则 substr 把它作为从字符串末尾开始的一个字符索引。如果 start 为负值且 abs(start) 大于字符串的长度，则 substr 使用 0 作为开始提取的索引。注意负的 start 参数不被 Microsoft JScript 所支持。

如果 length 为 0 或负值，则 substr 返回一个空字符串。如果忽略 length，则 substr 提取字符，直到字符串末尾。

```
var str = "abcdefghij";

console.log("(1,2): "    + str.substr(1,2));   // (1,2): bc
console.log("(-3,2): "   + str.substr(-3,2));  // (-3,2): hi
console.log("(-3): "     + str.substr(-3));    // (-3): hij
console.log("(1): "      + str.substr(1));     // (1): bcdefghij
console.log("(-20, 2): " + str.substr(-20,2)); // (-20, 2): ab
console.log("(20, 2): "  + str.substr(20,2));  // (20, 2):
```

### str.substring(indexStart[, indexEnd])

> 返回字符串两个索引之间（或到字符串末尾）的子串。

- indexStart: 一个 0 到字符串长度之间的整数。
- indexEnd: 可选。一个 0 到字符串长度之间的整数。

substring 提取从 indexStart 到 indexEnd（不包括）之间的字符。特别地：

1. 如果 indexStart 等于 indexEnd，substring 返回一个空字符串。
2. 如果省略 indexEnd，substring 提取字符一直到字符串末尾。
3. 如果任一参数小于 0 或为 NaN，则被当作 0。
4. 如果任一参数大于 stringName.length，则被当作 stringName.length。
5. 如果 indexStart 大于 indexEnd，则 substring 的执行效果就像两个参数调换了一样。例如，str.substring(1, 0) == str.substring(0, 1)。

```
var anyString = "Mozilla";

// 输出 "Moz"
console.log(anyString.substring(0,3));
console.log(anyString.substring(3,0));
console.log(anyString.substring(3,-3));
console.log(anyString.substring(3,NaN));
console.log(anyString.substring(-2,3));
console.log(anyString.substring(NaN,3));

// 输出 "lla"
console.log(anyString.substring(4,7));
console.log(anyString.substring(7,4));

// 输出 ""
console.log(anyString.substring(4,4));

// 输出 "Mozill"
console.log(anyString.substring(0,6));

// 输出 "Mozilla"
console.log(anyString.substring(0,7));
console.log(anyString.substring(0,10));
```

### str.slice(beginSlice[, endSlice])

> 提取字符串的一部分，并返回这个新字符串

- beginSlice: 从该索引（以 0 为基数）处开始提取原字符串中的字符。如果值为负数，会被当做 sourceLength + beginSlice 看待，这里的sourceLength 是字符串的长度 (例如， 如果beginSlice 是 -3 则看作是: sourceLength - 3)
- endSlice: 可选。在该索引（以 0 为基数）处结束提取字符串。如果省略该参数，slice会一直提取到字符串末尾。如果该参数为负数，则被看作是 sourceLength + endSlice，这里的 sourceLength 就是字符串的长度(例如，如果 endSlice 是 -3，则是, sourceLength - 3)。

slice() 从一个字符串中提取字符串并返回新字符串。在一个字符串中的改变不会影响另一个字符串。也就是说，slice 不修改原字符串，只会返回一个包含了原字符串中部分字符的新字符串。

注意：slice() 提取的新字符串包括beginSlice但不包括 endSlice。

例1：str.slice(1, 4) 提取新字符串从第二个字符到第四个 (字符索引值为 1, 2, 和 3)。

例2：str.slice(2, -1) 提取第三个字符到倒数第二个字符

```
var str1 = 'The morning is upon us.';
var str2 = str1.slice(4, -2);

console.log(str2); // OUTPUT: morning is upon u

str.slice(-3);     // returns 'us.'
str.slice(-3, -1); // returns 'us'
str.slice(0, -1);  // returns 'The morning is upon us'
```

## str.trim()

> 删除一个字符串两端的空白字符。在这个字符串里的空格包括所有的空格字符 (space, tab, no-break space 等)以及所有的行结束符（如 LF，CR）。

trim() 方法并不影响原字符串本身，它返回的是一个新的字符串。

```
var orig = '   foo  ';
console.log(orig.trim()); // 'foo'

// 另一个.trim()例子，只从一边删除

var orig = 'foo    ';
console.log(orig.trim()); // 'foo'
```

**变换类**

## str.split([separator][, limit])

> 将字符串分成子字符串，从而将一个String对象拆分为一个字符串数组。

- separator: 指定用来分割字符串的字符（串）。separator 可以是一个字符串或正则表达式。 如果忽略 separator，则返回整个字符串的数组形式。如果 separator 是一个空字符串，则 str 将会把原字符串中每个字符的数组形式返回。
- limit: 一个整数，限定返回的分割片段数量。split 方法仍然分割每一个匹配的 separator，但是返回的数组只会截取最多 limit 个元素。

split 方法返回一个数组。

当找到一个 seperator 时，separator 会从字符串中被移除，返回存进一个数组当中的子字符串。如果忽略 separator 参数，则返回的数组包含一个元素，该元素是原字符串。如果 separator 是一个空字符串，则 str 将被转换为由字符串中字符组成的一个数组。

如果 separator 是一个正则表达式，且包含捕获括号（capturing parentheses），则每次匹配到 separator 时，捕获括号匹配的结果将会插入到返回的数组中。然而，不是所有浏览器都支持该特性。

```
// 使用指定的分隔符将一个字符串分割成一个字符串数组。分隔字符串后，该函数依次输出原始字符串信息，被使用的分隔符，返回数组元素的个数，以及返回数组中所有的元素。

function splitString(stringToSplit, separator) {
  var arrayOfStrings = stringToSplit.split(separator);

  console.log('The original string is: "' + stringToSplit + '"');
  console.log('The separator is: "' + separator + '"');
  console.log("The array has " + arrayOfStrings.length + " elements: ");

  for (var i=0; i < arrayOfStrings.length; i++)
    console.log(arrayOfStrings[i] + " / ");
}

var tempestString = "Oh brave new world that has such people in it.";
var monthString = "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec";

var space = " ";
var comma = ",";

splitString(tempestString, space);
splitString(tempestString);
splitString(monthString, comma);

// ----------------------------------

The original string is: "Oh brave new world that has such people in it."
The separator is: " "
The array has 10 elements: Oh / brave / new / world / that / has / such / people / in / it. /

The original string is: "Oh brave new world that has such people in it."
The separator is: "undefined"
The array has 1 elements: Oh brave new world that has such people in it. /

The original string is: "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec"
The separator is: ","
The array has 12 elements: Jan / Feb / Mar / Apr / May / Jun / Jul / Aug / Sep / Oct / Nov / Dec /
```

