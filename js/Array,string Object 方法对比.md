 # Array

+ **Array.from()**：将 **类似数组**或**可迭代对象** 转化为数组，不会改变原	数组,返回一个新的[`数组`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array)实例。

  ```js
  console.log(Array.from('foo')); // expected output: Array ["f", "o", "o"]
  console.log(Array.from([1, 2, 3], x => x + x)); // expected output: Array [2, 4, 6]
  ```

+ **Array.isArray() ** determines whether the passed value is an 

  ```js
  Array.isArray([1, 2, 3]);  // true
  Array.isArray({foo: 123}); // false
  Array.isArray('foobar');   // false
  Array.isArray(undefined);  // false
  ```

+ **Array.of()**：方法创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型。

  ```js
  Array.of(7);       // [7] 
  Array.of(1, 2, 3); // [1, 2, 3]
  
  Array(7);          // [ , , , , , , ]
  Array(1, 2, 3);    // [1, 2, 3]
  ```

​        注意：`Array.of()` 和 `Array` 构造函数之间的区别在于处理整数参数：`Array.of(7)` 创建一个具有单个元素 **7** 的数组，而 **`Array(7)`** 创建一个长度为7的空数组（**注意：**这是指一个有7个空位(empty)的数组，而不是由7个`undefined`组成的数组）。

+ **concat()**方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。

  ```
  const array1 = ['a', 'b', 'c'];
  const array2 = ['d', 'e', 'f'];
  const array3 = array1.concat(array2);
  
  console.log(array3);
  // expected output: Array ["a", "b", "c", "d", "e", "f"]
  ```

+ **copyWithin**:浅复制数组的一部分到同一数组中的另一个位置，并返回它，不会改变原数组的长度, 但会改变原数组

  ```js
  const array1 = ['a', 'b', 'c', 'd', 'e'];
  // copy to index 0 the element at index 3
  console.log(array1.copyWithin(0, 3, 4));
  // expected output: Array ["d", "b", "c", "d", "e"]
  
  // copy to index 1 all elements from index 3 to the end
  console.log(array1.copyWithin(1, 3));
  // expected output: Array ["d", "d", "e", "d", "e"]
  ```
  
+ **entries()** 方法返回一个新的**Array Iterator**对象，该对象包含数组中每个索引的键/值对。

  ```js
  const array1 = ['a', 'b', 'c'];
  
  const iterator1 = array1.entries();
  console.log(iterator1.next().value);
  // expected output: Array [0, "a"]
  
  console.log(iterator1.next().value);
  // expected output: Array [1, "b"]
  ```

+ **every()**方法测试一个数组内的所有元素是否都能通过某个指定函数的测试。它返回一个布尔值。

  **注意**：若收到一个空数组，此方法在一切情况下都会返回 `true`。

  ```
  const isBelowThreshold = (currentValue) => currentValue < 40;
  const array1 = [1, 30, 39, 29, 10, 13];
  console.log(array1.every(isBelowThreshold));
  // expected output: true
  ```

+ **fill()**: 方法用一个固定值填充一个数组中从起始索引到终止索引内的全部元素。不包括终止索引。

  ```
  const array1 = [1, 2, 3, 4];
  
  // fill with 0 from position 2 until position 4
  console.log(array1.fill(0, 2, 4));
  // expected output: [1, 2, 0, 0]
  
  // fill with 5 from position 1
  console.log(array1.fill(5, 1));
  // expected output: [1, 5, 5, 5]
  
  console.log(array1.fill(6));
  // expected output: [6, 6, 6, 6]
  ```

+ **flat()** 方法会按照一个可指定的深度递归遍历数组，并将所有元素与遍历到的子数组中的元素合并为一个新数组返回。

  ```
  const arr1 = [0, 1, 2, [3, 4]];
  
  console.log(arr1.flat());
  // expected output: [0, 1, 2, 3, 4]
  
  const arr2 = [0, 1, 2, [[[3, 4]]]];
  
  console.log(arr2.flat(2));
  // expected output: [0, 1, 2, [3, 4]]
  ```

+ **reverse()** 方法将数组中元素的位置颠倒，并返回该数组。数组的第一个元素会变成最后一个，数组的最后一个元素变成第一个。该方法会改变原数组。

+ **pop()**方法从数组中删除最后一个元素，并返回该元素的值。此方法更改数组的长度。

+ **shift()** 方法从数组中删除**第一个**元素，并返回该元素的值。此方法更改数组的长度。

+ **slice()**方法返回一个新的数组对象，这一对象是一个由 `begin` 和 `end` 决定的原数组的**浅拷贝**（包括 `begin`，不包括`end`）。原始数组不会被改变。

  ```
  const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];
  
  console.log(animals.slice(2));
  // expected output: Array ["camel", "duck", "elephant"]
  
  console.log(animals.slice(2, 4));
  // expected output: Array ["camel", "duck"]
  
  console.log(animals.slice(1, 5));
  // expected output: Array ["bison", "camel", "duck", "elephant"]
  ```

  

+ **`splice()`** 方法通过删除或替换现有元素或者原地添加新的元素来修改数组,并以数组形式返回被修改的内容。此方法会改变原数组。

  ```
  const months = ['Jan', 'March', 'April', 'June'];
  months.splice(1, 0, 'Feb');
  
  第一个参数：开始位置；第二个参数：deleteCount，要删除的个数，第三个参数：item，表示要添加的新数目
  ```

  

# String

+ **slice()** 方法提取某个字符串的一部分，并返回一个新的字符串，且不会改动原字符串。

  ```
  str.slice(beginIndex[, endIndex])
  const str = 'The quick brown fox jumps over the lazy dog.';
  
  console.log(str.slice(31));
  // expected output: "the lazy dog."
  
  console.log(str.slice(4, 19));
  // expected output: "quick brown fox"
  ```

  ###  

+ **charAt()** 方法从一个字符串中返回指定的字符。

+ `**charCodeAt()**` 方法返回 `0` 到 `65535` 之间的整数，表示给定索引处的 UTF-16 代码单元

+ **`concat()`** 方法将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回。

+ `**endsWith()**`方法用来判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 `true` 或 `false`。

+  **`match()`** 方法检索返回一个字符串匹配正则表达式的结果。

+ **`matchAll()`** 方法返回一个包含所有匹配正则表达式的结果及分组捕获组的迭代器。

+ **`padEnd()`** 方法会用一个字符串填充当前字符串（如果需要的话则重复填充），返回填充后达到指定长度的字符串。从当前字符串的末尾（右侧）开始填充。

  ```
  'abc'.padEnd(10);          // "abc       "
  'abc'.padEnd(10, "foo");   // "abcfoofoof"
  'abc'.padEnd(6, "123456"); // "abc123"
  'abc'.padEnd(1);           // "abc"
  ```

+ **`padStart()`** 方法用另一个字符串填充当前字符串(如果需要的话，会重复多次)，以便产生的字符串达到给定的长度。从当前字符串的左侧开始填充。

  ```
  'abc'.padStart(10);         // "       abc"
  'abc'.padStart(10, "foo");  // "foofoofabc"
  'abc'.padStart(6,"123465"); // "123abc"
  'abc'.padStart(8, "0");     // "00000abc"
  'abc'.padStart(1);          // "abc"
  ```

+ **`repeat()`** 构造并返回一个新字符串，该字符串包含被连接在一起的指定数量的字符串的副本。

  ```js
  "abc".repeat(-1)     // RangeError: repeat count must be positive and less than inifinity
  "abc".repeat(0)      // ""
  "abc".repeat(1)      // "abc"
  "abc".repeat(2)      // "abcabc"
  "abc".repeat(3.5)    // "abcabcabc" 参数count将会被自动转换成整数.
  "abc".repeat(1/0)    // RangeError: repeat count must be positive and less than inifinity
  ```

+ **`replace()`** 方法返回一个由替换值（`replacement`）替换部分或所有的模式（`pattern`）匹配项后的新字符串。

  ```
  const p = 'The quick brown fox jumps over the lazy dog. If the dog reacted, was it really lazy?';
  
  const regex = /dog/gi;
  
  console.log(p.replace(regex, 'ferret'));
  // expected output: "The quick brown fox jumps over the lazy ferret. If the ferret reacted, was it really lazy?"
  
  console.log(p.replace('dog', 'monkey'));
  // expected output: "The quick brown fox jumps over the lazy monkey. If the dog reacted, was it really lazy?"
  ```

+ **`search()`** 方法执行正则表达式和 [`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String) 对象之间的一个搜索匹配。必须传入正则表达式，如果传入一个非正则表达式对象 `regexp`，则会使用 `new RegExp(regexp)` 隐式地将其转换为正则表达式对象。如果匹配成功，则 `search()` 返回正则表达式在字符串中首次匹配项的索引;否则，返回 `-1`。

+ **split()** 方法使用指定的分隔符字符串将一个[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String)对象分割成子字符串数组，以一个指定的分割字串来决定每个拆分的位置。 

  ```
  const str = 'The quick brown fox jumps over the lazy dog.';
  
  const words = str.split(' ');
  console.log(words[3]);
  // expected output: "fox"
  ```

+ **`substring() `**方法返回一个字符串在开始索引到结束索引之间的一个子集, 或从开始索引直到字符串的末尾的一个子集。如果 `indexStart` 大于 `indexEnd`，则 `substring` 的执行效果就像两个参数调换了一样。

  所以slice 和substring() 的区别：

   当接收的参数是负数时，slice会将它字符串的长度与对应的负数相加，结果作为参；substring则干脆将负参数都直接转换为0。



# Object

+ **Object.assign()** 方法用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。

```
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget);
// expected output: Object { a: 1, b: 4, c: 5 }

```

会改变第一个参数target

+ **`Object.create()`**方法创建一个新对象，使用现有的对象来提供新创建的对象的__proto__。一个新对象，带着指定的原型对象和属性。

  ```js
  const person = {
    isHuman: false,
    printIntroduction: function() {
      console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
    }
  };
  
  const me = Object.create(person);
  
  me.name = 'Matthew'; // "name" is a property set on "me", but not on "person"
  me.isHuman = true; // inherited properties can be overwritten
  
  me.printIntroduction();
  // expected output: "My name is Matthew. Am I human? true"
  console.log(me.__proto__)
  ```

+ **`Object.defineProperties(obj, props)`** 方法直接在一个对象上定义新的属性或修改现有属性，并返回该对象。

```js
var obj = {};
Object.defineProperties(obj, {
  'property1': {
    value: true,
    writable: true
  },
  'property2': {
    value: 'Hello',
    writable: false
  }
  // etc. etc.
});
```

+ **Object.defineProperty()** 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性，并返回此对象。

  ```
  const object1 = {};
  
  Object.defineProperty(object1, 'property1', {
    value: 42,
    writable: false
  });
  
  object1.property1 = 77;
  // throws an error in strict mode
  
  console.log(object1.property1);
  // expected output: 42
  
  ```

* **Object.entries()**`方法返回一个给定对象自身可枚举属性的键值对数组，其排列与使用 [`for...in](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...in) 循环遍历该对象时返回的顺序一致（区别在于 for-in 循环还会枚举原型链中的属性）。

```
const object1 = {
  a: 'somestring',
  b: 42
};
console.log( Object.entries(object1)) // Array [Array ["a", "somestring"], Array ["b", 42]]
for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}

// expected output:
// "a: somestring"
// "b: 42"
// order is not guaranteed
```

+ **Object.freeze()** 方法可以**冻结**一个对象。一个被冻结的对象再也不能被修改；冻结了一个对象则不能向这个对象添加新的属性，不能删除已有属性，不能修改该对象已有属性的可枚举性、可配置性、可写性，以及不能修改已有属性的值。此外，冻结一个对象后该对象的原型也不能被修改。`freeze()` 返回和传入的参数相同的对象。

```
const obj = {
  prop: 42
};

Object.freeze(obj);

obj.prop = 33;
// Throws an error in strict mode

console.log(obj.prop);
// expected output: 42

```

在ES5中，如果这个方法的参数不是一个对象（一个原始值），那么它会导致 [`TypeError`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypeError)。在ES2015中，非对象参数将被视为要被冻结的普通对象，并被简单地返回。

**note： 只能冻结一层**

+ **Object.isFrozen(obj)**`方法判断一个对象是否被[冻结](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze)。

+ **Object.seal()**`方法封闭一个对象，阻止添加新属性并将所有现有属性标记为不可配置。当前属性的值只要原来是可写的就可以改变。

  用`Object.seal()`密封的对象可以改变它们现有的属性。使用`Object.freeze()` 冻结的对象中现有属性是不可变的。

  ```
  const object1 = {
    property1: 42
  };
  
  Object.seal(object1);
  object1.property1 = 33;
  console.log(object1.property1);
  // expected output: 33
  
  delete object1.property1; // cannot delete when sealed
  console.log(object1.property1);
  // expected output: 33
  ```

  

+ **`Object.isSealed(obj)`** 方法判断一个对象是否被密封。如果这个对象是密封的，则返回 `true`，否则返回 `false`。密封对象是指那些不可 [`扩展`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/isExtensible) 的，且所有自身属性都不可配置且因此不可删除（但不一定是不可写）的对象。

+  **Object.fromEntries()**` 方法把键值对列表转换为一个对象。

```
const entries = new Map([
  ['foo', 'bar'],
  ['baz', 42]
]);

const obj = Object.fromEntries(entries);

console.log(obj);
// expected output: Object { foo: "bar", baz: 42 }

```

+ **`Object.getOwnPropertyDescriptor()`** 方法返回指定对象上一个自有属性对应的属性描述符。（自有属性指的是直接赋予该对象的属性，不需要从原型链上进行查找的属性）

```
const object1 = {
  property1: 42
};

const descriptor1 = Object.getOwnPropertyDescriptor(object1, 'property1');

console.log(descriptor1.configurable);
// expected output: true

console.log(descriptor1.value);
// expected output: 42
```

+ **Object.getOwnPropertyDescriptors()** 方法用来获取一个对象的所有自身属性的描述符。

+ **`Object.getOwnPropertyNames()`**方法返回一个由指定对象的所有自身属性的属性名（包括不可枚举属性但不包括Symbol值作为名称的属性）组成的数组。
+ **Object.getOwnPropertySymbols()**` 方法返回一个给定对象自身的所有 Symbol 属性的数组。

+ **Object.getPrototypeOf()**` 方法返回指定对象的原型（内部`[[Prototype]]`属性的值）。

```js
const prototype1 = {};
const object1 = Object.create(prototype1);

console.log(Object.getPrototypeOf(object1) === prototype1);
// expected output: true
```

给定对象的原型。如果没有继承属性，则返回 null 。

+ **Object.is(value1, value2)**` 方法判断两个值是否为[同一个值](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Equality_comparisons_and_sameness)。详情见参考文档

+ **Object.isExtensible()** 方法判断一个对象是否是可扩展的（是否可以在它上面添加新的属性）

+ **Object.keys()**方法会返回一个由一个给定对象的自身可枚举属性组成的数组，数组中属性名的排列顺序和正常循环遍历该对象时返回的顺序一致 。

```
// simple array
var arr = ['a', 'b', 'c'];
console.log(Object.keys(arr)); // console: ['0', '1', '2']

// array like object
var obj = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.keys(obj)); // console: ['0', '1', '2']

// array like object with random key ordering
var anObj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.keys(anObj)); // console: ['2', '7', '100']
```

+ **Object.values()**`方法返回一个给定对象自身的所有可枚举属性值的数组，值的顺序与使用[`for...in`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...in)循环的顺序相同 ( 区别在于 for-in 循环枚举原型链中的属性 )。

  ```
  var obj = { foo: 'bar', baz: 42 };
  console.log(Object.values(obj)); // ['bar', 42]
  
  // array like object
  var obj = { 0: 'a', 1: 'b', 2: 'c' };
  console.log(Object.values(obj)); // ['a', 'b', 'c']
  
  // array like object with random key ordering
  // when we use numeric keys, the value returned in a numerical order according to the keys
  var an_obj = { 100: 'a', 2: 'b', 7: 'c' };
  console.log(Object.values(an_obj)); // ['b', 'c', 'a']
  
  // getFoo is property which isn't enumerable
  var my_obj = Object.create({}, { getFoo: { value: function() { return this.foo; } } });
  my_obj.foo = 'bar';
  console.log(Object.values(my_obj)); // ['bar']
  
  // non-object argument will be coerced to an object
  console.log(Object.values('foo')); // ['f', 'o', 'o']
  ```

  

+ **Object.preventExtensions()**`方法让一个对象变的不可扩展，也就是永远不能再添加新的属性。

```
const object1 = {};

Object.preventExtensions(object1);

try {
  Object.defineProperty(object1, 'property1', {
    value: 42
  });
} catch (e) {
  console.log(e);
  // expected output: TypeError: Cannot define property property1, object is not extensible
}
```

注意，一般来说，不可扩展对象的属性可能仍然可被*删除*。

+ **object.prototype.hasOwnProperty()**` 方法会返回一个布尔值，指示对象自身属性中是否具有指定的属性（也就是，是否有指定的键）

  ```js
  const object1 = {};
  object1.property1 = 42;
  
  console.log(object1.hasOwnProperty('property1'));
  // expected output: true
  
  console.log(object1.hasOwnProperty('toString'));
  // expected output: false
  
  console.log(object1.hasOwnProperty('hasOwnProperty'));
  ```

+ **object.prototype.isPrototypeOf(object)**` 方法用于测试一个对象是否存在于另一个对象的原型链上。

+ **object.prototype.valueOf(object)**` 方法返回指定对象的原始值。

  ```js
  // Array：返回数组对象本身
  var array = ["ABC", true, 12, -5];
  console.log(array.valueOf() === array);   // true
  
  // Date：当前时间距1970年1月1日午夜的毫秒数
  var date = new Date(2013, 7, 18, 23, 11, 59, 230);
  console.log(date.valueOf());   // 1376838719230
  
  // Number：返回数字值
  var num =  15.26540;
  console.log(num.valueOf());   // 15.2654
  
  // 布尔：返回布尔值true或false·
  var bool = true;
  console.log(bool.valueOf() === bool);   // true
  
  // new一个Boolean对象
  var newBool = new Boolean(true);
  // valueOf()返回的是true，两者的值相等
  console.log(newBool.valueOf() == newBool);   // true
  // 但是不全等，两者类型不相等，前者是boolean类型，后者是object类型
  console.log(newBool.valueOf() === newBool);   // false
  ```

  

+ **Object.setPrototypeOf(obj, prototype)** 设置一个指定的对象的原型 ( 即, 内部[[Prototype]]属性）到另一个对象或  [`null`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/null)。

  注意：由于现代 JavaScript 引擎优化属性访问所带来的特性的关系，更改对象的 `[[Prototype]]`在***各个***浏览器和 JavaScript 引擎上都是一个很慢的操作。其在更改继承的性能上的影响是微妙而又广泛的，这不仅仅限于 `obj.__proto__ = ...` 语句上的时间花费，而且可能会延伸到***任何***代码，那些可以访问***任何***`[[Prototype]]`已被更改的对象的代码。如果你关心性能，你应该避免设置一个对象的 `[[Prototype]]`。相反，你应该使用 [`Object.create()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/create)来创建带有你想要的`[[Prototype]]`的新对象。 

# Function

+ **length** 属性指明函数的形参个数。

```js
function func1() {}

function func2(a, b) {}

console.log(func1.length);
// expected output: 0

console.log(func2.length);
// expected output: 2

```

+ **function\.name** 属性返回函数实例的名称。

+ **apply()** 方法调用一个具有给定`this`值的函数，以及以一个数组（或[类数组对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Indexed_collections#Working_with_array-like_objects)）的形式提供的参数。

 **注意：**call()方法的作用和 apply() 方法类似，区别就是`call()`方法接受的是**参数列表**，而`apply()`方法接受的是**一个参数数组**。

func.apply(thisArg, [argsArray]):  thisArg必选的. 在 *`func`* 函数运行时使用的 `this` 值.

```js
const numbers = [5, 6, 2, 3, 7];

const max = Math.max.apply(null, numbers);

console.log(max);
// expected output: 7

const min = Math.min.apply(null, numbers);

console.log(min);
// expected output: 2
```

+ **bind()** 方法创建一个新的函数，在 `bind()` 被调用时，这个新函数的 `this` 被指定为 `bind()` 的第一个参数，而其余参数将作为新函数的参数，供调用时使用

```js
const module = {
  x: 42,
  getX: function() {
    return this.x;
  }
};

const unboundGetX = module.getX;
console.log(unboundGetX()); // The function gets invoked at the global scope
// expected output: undefined

const boundGetX = unboundGetX.bind(module);
console.log(boundGetX());
// expected output: 42
```

+ **`toString()`** 方法返回一个表示当前函数源代码的字符串。





问题：Array.isArray() 和  instanceof Array 的区别？

+ Array.isArray() es5 的方法，不支持ie8以下的浏览器

+  当检测Array实例时，`Array.isArray` 优于 `instanceof` ，instanceof 不支持iframe的窗口对象的数组创建的数组

+ instanceof 的内部机制是通过判断对象的原型链中是不是能找到类型的 prototype。使用instanceof 会判断对应的原型链上是否有对应的Array 原型 

  ```
  []  instanceof Array; // true  
  []  instanceof Object; // true
  ```

  instanceof 只能用来判断对象类型，原始类型不可以。并且所有对象类型 instanceof Object 都是 true。



总结：万能的判断方法, 对所有类型都可判断，即使是null 和undefined

```
Object.prototype.toString.call(xx)
```

