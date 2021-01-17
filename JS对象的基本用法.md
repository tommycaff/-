# JS 对象基本用法

## 声明对象的两种语法

第一种，常用的声明语法

```
let obj = {
  name: "niHao",
  age: 18
};
```

第二种，正式的写法

```
let obj = {
  name: "niHao",
  age: 18
};
```
**细节**

* 键名是字符串，不是标识符，可以包含任意字符
* 引号可省略，省略后就只能写标识符
* 就算引号省略了，键名还是字符串

## 如何删除对象的属性

使用操作符`delete`即可：

```
delete obj.xxx;
// 或
delete obj["xxx"];
```

## 如何查看对象的属性

```
Object.keys(obj); // 查看自身所有属性

console.dir(obj); // 查看自身 + 共用属性

// 另外两种查看属性的方法
obj["key"]; // 中括号语法

obj.key; // 点语法

obj[key]; // 此 key 为变量，不一定为 'key'
```

**注意**：obj.name等价于obj['name']（两者都是指代obj的属性name）
obj.name不等价于obj[name]（后者指代的是obj中name变量所代表的属性，不一定是名为name）

## 如何修改或增加对象的属性

```
// 直接赋值
let obj = {
    name: 'niHao'
}

obj.name = 'niHao'

obj['name'] = 'niHao'

obj['na' + 'me'] = 'niHao'

// 批量赋值
Object.assign(obj, {
    age: 18,
    gender: 'man'
})
```

## 'name' in obj 和 obj.hasOwnProperty('name') 的区别

正如`hasOwnProperty`所写，该方法可以判断该属性，是否是obj所独自拥有的
而`in`操作符，是包括了obj 隐藏属性中是否也含有该属性
语句有很多种类：赋值语句、函数调用语句、声明语句等等
