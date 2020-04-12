# JavaScript 原生数据类型

### Object
---
1. Object.assign()   
   方法用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。相同的属性，后面的属性覆盖前面的。
#### 语法
> Object.assign(target, ...sources)

---
2. Object.create()

```
let obj = Object.create(Object.prototype, {
  // foo会成为所创建对象的数据属性
  foo: { 
    writable:true,
    configurable:true,
    value: "hello" 
  },
  // bar会成为所创建对象的访问器属性
  bar: {
    configurable: false,
    get: function() { return 10 },
    set: function(value) {
      console.log("Setting `o.bar` to", value);
    }
  }
});
```

#### 语法
> Object.create(proto[, propertiesObject])   
proto:新创建对象的原型对象。   
propertiesObject: 对象的属性描述符以及相应的属性名称

---

3. Object.defineProperty()  
   方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性，并返回此对象。

#### 语法
> Object.defineProperty(obj, prop, descriptor)   
  obj:要定义属性的对象。  
  prop:要定义或修改的属性的名称或 Symbol   
  descriptor: 被传递给函数的对象。

  - configurable  
  当且仅当该属性的 configurable 键值为 true 时，该属性的描述符才能够被改变，同时该属性也能从对应的对象上被删除。默认为 false。
- enumerable  
  当且仅当该属性的 enumerable 键值为 true 时，该属性才会出现在对象的枚举属性中。默认为 false。
- value   
  该属性对应的值。可以是任何有效的 JavaScript 值（数值，对象，函数等）。
  默认为 undefined。
- writable  
当且仅当该属性的 writable 键值为 true 时，属性的值，也就是上面的 value，才能被赋值运算符改变。
默认为 false
- get  
属性的 getter 函数，如果没有 getter，则为 undefined。当访问该属性时，会调用此函数。执行时不传入任何参数，但是会传入 this 对象（由于继承关系，这里的this并不一定是定义该属性的对象）。该函数的返回值会被用作属性的值。
默认为 undefined。
- set  
属性的 setter 函数，如果没有 setter，则为 undefined。当属性值被修改时，会调用此函数。该方法接受一个参数（也就是被赋予的新值），会传入赋值时的 this 对象。
默认为 undefined。

---
4. Object.defineProperties()   
   方法直接在一个对象上定义多个新的属性或修改现有属性，并返回该对象。

#### 语法
>Object.defineProperties(obj, props)

---
5. Object.freeze()  
  方法可以冻结一个对象。一个被冻结的对象再也不能被修改；冻结了一个对象则不能向这个对象添加新的属性，不能删除已有属性，不能修改该对象已有属性的可枚举性、可配置性、可写性，以及不能修改已有属性的值。此外，冻结一个对象后该对象的原型也不能被修改。freeze() 返回和传入的参数相同的对象。
#### 语法
> Object.freeze(obj)
---
6.Object.isFrozen()     
方法判断一个对象是否被冻结。
#### 语法
> Object.isFrozen(obj)
---
7. Object.seal()  
方法封闭一个对象，阻止添加新属性并将所有现有属性标记为不可配置。当前属性的值只要原来是可写的就可以改变。
#### 语法
>Object.seal(obj)   
obj:将要被密封的对象。

- Object.isSealed()   
方法判断一个对象是否被密封
#### 语法
> Object.isSealed(obj)   
obj:要被检查的对象。

**对比 Object.freeze()   
使用Object.freeze()冻结的对象中的现有属性值是不可变的。用Object.seal()密封的对象可以改变其现有属性值。**
---
- Object.preventExtensions()   
方法让一个对象变的不可扩展，也就是永远不能再添加新的属性。
#### 语法
> Object.preventExtensions(obj)   

Object.preventExtensions()仅阻止添加自身的属性。但属性仍然可以添加到对象原型。

- Object.isExtensible()   
方法判断一个对象是否是可扩展的（是否可以在它上面添加新的属性）。
#### 语法
> Object.isExtensible(obj)

---

6. Object.keys()  
方法会返回一个由一个给定对象的自身可枚举属性组成的数组，数组中属性名的排列顺序和使用 for...in 循环遍历该对象时返回的顺序一致 。
#### 语法
> Object.keys(obj)

- Object.values()   
方法返回一个给定对象自身的所有可枚举属性值的数组，值的顺序与使用for...in循环的顺序相同 ( 区别在于 for-in 循环枚举原型链中的属性 )。
#### 语法
> Object.values(obj)

 - Object.entries()   
方法返回一个给定对象自身可枚举属性的键值对数组，其排列与使用 for...in 循环遍历该对象时返回的顺序一致（区别在于 for-in 循环还会枚举原型链中的属性）。
#### 语法
> Object.entries(obj)

- Object.fromEntries()  
方法把键值对列表转换为一个对象。
#### 语法
> Object.fromEntries(iterable);
```
const map = new Map([ ['foo', 'bar'], ['baz', 42] ]);
const obj = Object.fromEntries(map);
console.log(obj); // { foo: "bar", baz: 42 }
```
---
8 Object.getOwnPropertyDescriptor()   
方法返回指定对象上一个自有属性对应的属性描述符。（自有属性指的是直接赋予该对象的属性，不需要从原型链上进行查找的属性）

#### 语法
> Object.getOwnPropertyDescriptor(obj, prop)   
obj:需要查找的目标对象   
prop:目标对象内属性名称


---
9. Object.getOwnPropertyDescriptors()  
方法用来获取一个对象的所有自身属性的描述符。

#### 语法
> Object.getOwnPropertyDescriptors(obj)
---
10. Object.getOwnPropertyNames()   
方法返回一个由指定对象的所有自身属性的属性名（包括不可枚举属性但不包括Symbol值作为名称的属性）组成的数组。
#### 语法
> Object.getOwnPropertyNames(obj)
---
11. Object.getOwnPropertySymbols()   
方法返回一个给定对象自身的所有 Symbol 属性的数组。
#### 语法
> Object.getOwnPropertySymbols(obj)
---
12. Object.getPrototypeOf()   
方法返回指定对象的原型（内部[[Prototype]]属性的值）。
#### 语法
> Object.getPrototypeOf(object)
- Object.setPrototypeOf()  
方法设置一个指定的对象的原型 ( 即, 内部[[Prototype]]属性）到另一个对象或  null。
#### 语法
> Object.setPrototypeOf(obj, prototype)

---
13. Object.is()   
方法判断两个值是否是相同的值。
#### 语法
> Object.is(value1, value2);

---
---
**Object.prototype原型方法**
- hasOwnProperty()
#### 语法
> obj.hasOwnProperty(prop)   
prop:要检测的属性的 String 字符串形式表示的名称，或者 Symbol。

---
- isPrototypeOf()   
方法用于测试一个对象是否存在于另一个对象的原型链上。
#### 语法
> prototypeObj.isPrototypeOf(object)
```
console.log(Baz.prototype.isPrototypeOf(baz)); // true
```

---
- propertyIsEnumerable()   
方法返回一个布尔值，表示指定的属性是否可枚举。

#### 语法
> obj.propertyIsEnumerable(prop)  
prop:需要测试的属性名


### Function
- name
- apply  
方法调用一个具有给定this值的函数，以及作为一个数组（或类似数组对象）提供的参数。
#### 语法
> func.apply(thisArg, [argsArray])  
thisArg:
必选的。在 func 函数运行时使用的 this 值。请注意，this可能不是该方法看到的实际值：如果这个函数处于非严格模式下，则指定为 null 或 undefined 时会自动替换为指向全局对象，原始值会被包装。
argsArray:   
可选的。一个数组或者类数组对象，其中的数组元素将作为单独的参数传给 func 函数。如果该参数的值为 null 或  undefined，则表示不需要传入任何参数。从ECMAScript 5 开始可以使用类数组对象。 浏览器兼容性 请参阅本文底部内容。

[apply](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)

---
- call  
方法使用一个指定的 this 值和单独给出的一个或多个参数来调用一个函数。 
#### 语法
> function.call(thisArg, arg1, arg2, ...)   
thisArg:
可选的。在 function 函数运行时使用的 this 值。请注意，this可能不是该方法看到的实际值：如果这个函数处于非严格模式下，则指定为 null 或 undefined 时会自动替换为指向全局对象，原始值会被包装。   
arg1, arg2, ...:
指定的参数列表。
[call](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call)

---
- bind    
方法创建一个新的函数，在 bind() 被调用时，这个新函数的 this 被指定为 bind() 的第一个参数，而其余参数将作为新函数的参数，供调用时使用。

#### 语法
> function.bind(thisArg[, arg1[, arg2[, ...]]])   
thisArg:  调用绑定函数时作为 this 参数传递给目标函数的值。 如果使用new运算符构造绑定函数，则忽略该值。当使用 bind 在 setTimeout 中创建一个函数（作为回调提供）时，作为 thisArg 传递的任何原始值都将转换为 object。如果 bind 函数的参数列表为空，执行作用域的 this 将被视为新函数的 thisArg。  
arg1, arg2, ... :当目标函数被调用时，被预置入绑定函数的参数列表中的参数。
[bind](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)



### Array

### Set

### Map