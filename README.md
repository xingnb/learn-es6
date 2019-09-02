# es6个人学习demo

## demo01

### 安装babel 
`npm install -g babel-cli`  
`npm install --save-dev babel-preset-es2015 babel-cli` 
------------ 
添加**.babelrc**
```
{
    "presets":[
        "es2015"
    ],
    "plugins":[]
}
```
### 简化命令
```
"scripts": {
    "build": "babel src/index.js -o dist/index.js"
}
```

### 解构赋值

#### 数值的解构赋值
```let [d,e,f] = [0,1,2]```  
*数组模式和赋值模式统一：*  
*可以简单的理解为等号左边和等号右边的形式要统一，如果不统一解构将失败。*  
```let [a,[b,c],d]=[1,[2,3],4];```  
*解构赋值是允许你使用默认值的*  
```let [a,b='a',c='Q']=['Q']```  
*console.log(a+b+c); //控制台显示QaQ*  
#### 对象的解构赋值

```
let {foo,bar} = {foo:'JSPang',bar:'技术胖'};
console.log(foo+bar); //控制台打印出了“JSPang技术胖”
```
*注意：对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由它的位置决定；而对象的属性没有次序，变量必须与属性同名，才能取到正确的值。*  
*括号的使用*  
*如果在解构之前就定义了变量，使用括号*  
```
let foo;
({foo} ={foo:'JSPang'});
console.log(foo); //控制台输出jspang
```
#### 字符串的解构赋值

```
const [a,b,c,d,e,f]="JSPang";
console.log(a);
console.log(b);
console.log(c);
console.log(d);
console.log(e);
console.log(f);
```

### 扩展运算符
#### 函数传参
```
function jspang(...arg){
    console.log(arg[0]);
    console.log(arg[1]);
    console.log(arg[2]);
    console.log(arg[3]);
 
}
jspang(1,2,3);
```
*类似函数的内的**argument***

#### 拷贝数组
```
let arr1=['www','jspang','com'];
let arr2=[...arr1,'shengHongYu'];
console.log(arr2);
```

#### rest运算符
```
function jspang(first,...arg){
    console.log(arg.length);
}
jspang(0,1,2,3,4,5,6,7);
```

### 字符串模版

```
let jspang='技术胖';
let blog = `
<b>非常高兴你能看到这篇文章</b>，
我是你的老朋友${jspang}。
<br/>这节课我们学习字符串模版。`;
document.write(blog);
```
*字符串模板允许换行和添加html标签*  
-----------------------------
是否存在 includes  
开头是否存在 startsWith  
结尾是否存在 endsWith  
字符串复制 repeat  
```document.write('---'.repeat(30));```

### ES6数字操作
Number.isFinite()  
Number.isNaN()  
Number.isInteger()  
Number.parseInt()  
Number.parseFloat()  
Number.MAX_SAFE_INTEGER = Math.pow(2,53)-1
Number.MIN_SAFE_INTEGER = Math.pow(-2,53)-1
Number.isSafeInteger()  

### 数值知识
```
let  json = {
    '0': 'jspang',
    '1': '技术胖',
    '2': '大胖逼逼叨',
    length:3
}
 
let arr=Array.from(json);
console.log(arr)
```  
----------------------------- 
```
let arr =Array.of('技术胖','jspang','大胖逼逼叨');
```
-----------------------------  
```
let arr=[1,2,3,4,5,6,7,8,9];
arr.find((value,index,arr)=>{
    return value > 5;
})
```
value：表示当前查找的值。  
index：表示当前查找的数组索引。  
arr：表示当前数组。  

-----------------------------
array.fill(str,i,j) 包括 **i** ,不包括 **j**
```
let arr=[0,1,2,3];
arr.fill('web',1,3);
console.log(arr); // 输出[0,'web','web',3]
```
---------------------------------
```
let arr=['jspang','技术胖','大胖逼逼叨']
 
for (let item of arr){
    console.log(item);
}

for (let index of arr.keys()){
    console.log(index);
}

for (let [index,val] of arr.entries()){
    console.log(index+':'+val);
}
```
----------------------------------------
entries()实例方式生成的是Iterator形式的数组，那这种形式的好处就是可以让我们在需要时用next()手动跳转到下一个值
```
let arr=['jspang','技术胖','大胖逼逼叨']
let list=arr.entries();
console.log(list.next().value); // [0, "jspang"]
console.log(list.next().value); // [1, "技术胖"]
console.log(list.next().value); // [2, "大胖逼逼叨"]
```