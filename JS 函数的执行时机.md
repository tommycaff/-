# JS 函数的执行时机

## JS函数的调用时机不同，结果也不同
setTimeout()方法会设置一个计时器，该定时器在计时器终止后执行一个函数或指定的一段代码。


```
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}

```
上列代码打印出来的结果是6个6，这是为什么呢？
首先代码声明了一个全局变量i的值为0，在执行for循环，而for循环内部的代码是setTimeout(),delay的计时器为0，表示的是“马上”执行，或者尽快执行。每次for循环的时候，也会执行一次setTimeout()，待for循环结束后，在执行setTimeout()内的箭头函数，但是此时i的值已经随for循环自增变成了6，所以打印出的是6个6。
通过下列代码就可以打印出 0、1、2、3、4、5

```
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}


```
这是因为JS在for和let一起用时，每次for循环会多创建一个i，而setTimeout里的箭头函数输出的就是这个新的i。