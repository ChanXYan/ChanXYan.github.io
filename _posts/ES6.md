# ES6

#### 防止重复定义

let : 生命周期在所在块内  , 不能重复声明

const : 只是保持指向地址的指针不变


- 所以固定对象不能使用const, 而是使用freeze

  ```js
  彻底冻结
  var constantize = (obj) => {
    Object.freeze(obj);
    Object.keys(obj).forEach( (key, i) => {
      if ( typeof obj[key] === 'object' ) {
        constantize( obj[key] );
      }
    });
  };
  ```

#### for循环

有一个特别之处，就是: 设置循环变量的那部分是一个父作用域，而循环体内部是一个单独的子作用域

#### 解构赋值: 支持批量赋值, 模式匹配, 解构赋值

数组赋值: 各种各样(包括literator ,  set结构)

对象赋值: 必须属性同名, 才能赋值

###### 好处

查询结果的时候直接把需要的数据拉出来

##### 写法:两边结构一样, 右边必得是个东西, 赋值和解构同时完成

右边不能是undefinded/null/奇奇怪怪





#### 闭包是块级作用域没有的时候出来的临时解决方案

```js
(function(){
    //for循环
})(i);
```

#### 函数的扩展

##### ...

- 收集 ...c)

  剩余的都算c, 没剩的就是[]

- 展开数组/json ...arr

  一个个展开a,b,c

把内容啪唧拍在这

##### array的map,reduce,fliter,foreach

- map(item,index): 映射, 操作添加映射值, 键值对
- reduce(temp,item,index): 进去几个出来一个(求和,求均值等)
- fliter: 字面意思
- foreach: 进去几个出来几个(循环)

> **Map**
>
> （1）size 属性，返回 Map 结构的成员总数
> （2）set(key, value)，设置键名key对应的键值为value
> （3）get(key)，读取key对应的键值，如果找不到key，返回undefined。
> （4）has(key)，表示某个键是否在当前 Map 对象之中。
> （5）delete(key)，delete方法删除某个键，返回true。如果删除失败，返回false。
> （6） clear()，清除所有成员，没有返回值。
>
> keys()：返回键名的遍历器。
> values()：返回键值的遍历器。
> entries()：返回所有成员的遍历器。
> forEach()：遍历 Map 的所有成员。



```js
let a = arr.map
```



##### 箭头函数

- 一个参数可以不写

- 函数里面只有一句return可以不写`{return}`

- 修正this

  > 将this固定到当前环境上(对象里)

##### 函数默认值

1. 默认声明, 内部不需要再次声明

2. 不能同名

3. 与解构赋值结合:<img src="D:\note\技术了解.assets\image-20201210114404078.png" alt="image-20201210114404078" style="zoom:80%;" />

   - json一定的给的对象, 哪怕是空的

4. 尾部参数有默认值可以省略, 其他不行

   所以开发时, 默认值放在最后面, 最多默认的放在最后面; 实在有需要, 可以传入`undefined`显式激活



#### promise

```js
const promise =new Promise((resolve, reject) => {
      if(1){
        resolve(value)
      }else {
        reject(error)
      }
    }).then(//状态改变时的回调
      value => {
      //success
    },error=>{
      //failure
    }).catch(//出现错误时的回调
      //deal whit error
    ).finally(//anyway,最后都会用到的函数
      //final operation
    )
```

#### async

generator语法糖

> **优点:**
>
> async 函数的实现原理，就是将 Generator 函数和自动执行器，包装在一个函数里。
> async函数对 Generator 函数的改进，体现在以下四点:
> （1）内置执行器。
> （2）更好的语义。
> async和await，比起星号和yield，语义更清楚了。
> （3）更广的适用性。
> co模块约定，yield命令后面只能是 Thunk 函数或 Promise 对象，而async函数的await命令后面，可以是 Promise 对象和原始类型的值
> （4）返回值是 Promise。
> async函数的返回值是 Promise 对象，这比 Generator 函数的返回值是 Iterator 对象方便，可以用then方法指定下一步的操作。
>
> **使用:**
>
> await命令后面是一个 Promise 对象，返回该对象的结果。如果不是 Promise 对象，就直接返回对应的值。
> 任何一个await语句后面的 Promise 对象变为reject状态，那么整个async函数都会中断执行。可以将需判断的await放再try…catch结构里面，不管这个异步操作是否成功，接下来的await都会执行。

#### class

- class extends 的时候, 儿子需要使用 `super()` 将 `this` 从父亲那里拿过来

  ES6 要求，子类的构造函数必须执行一次`super`

  作为函数时，`super()`只能用在子类的构造函数之中，其他会报错

  作为对象时，`super()`在普通方法中---指向父类的原型对象；在静态方法中---指向父类 ;  但无法使用父类实例的方法和属性, 只可以使用父类原型的

  > 指向父类和指向父类原型的不同是: 指向父类可以读取到父类的静态函数, 而父类原型只可以读取到原型上的方法

# es6-blue

Java是公认的语法最合理的，最严谨的

- js终于迎来了一个“正常”的变量`let`, 还有`const`
- js终于迎来了类`class`
- 

