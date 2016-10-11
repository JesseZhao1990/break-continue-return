#总结js中的 break continue return

##在 break,continue和return 三个关键字中， break,continue是一起的。
用在循环中精确控制代码的执行。其中，break语句会立即退出循环。而continue语句虽然也是立即退出循环。但是退出循环后会从循环的顶部继续执行，也就是说只会退出本次循环。

体会下面的两个例子

例子1：[演示地址](http://codepen.io/zhaojianxin/pen/kkJGOY)

```
var num = 0;

for(var i=1;i<10;i++){
  if(i==5){
    break;
  }
  num++;
}
alert(num);   //4

```
为什么num只是4. 因为i等于5的时候退出了for循环。


例子2：[演示地址](http://codepen.io/zhaojianxin/pen/ORkxKo)

```
var num = 0;

for(var i=1;i<10;i++){
  if(i==5){
    continue;
  }
  num++;
}
alert(num);   //8

```
为什么num等于8呢？因为除了i=5的时候跳出了循环其他次都执行了循环体。共执行了8次

**那现在有一个问题。如果是两层for循环的嵌套。想跳出循环怎么办？这时就必须借助于label了**

**思考一下开心消消乐是怎么算的？相邻的相同颜色要爆炸消失，是不是可以用到break**

**switch中的break也是同样的道理,体会下面的两个例子**

例子1：[演示地址](http://codepen.io/zhaojianxin/pen/dpZkGk)

```
i=10
switch(i){
  case 10:
    alert("10");
    break;
  case 11:
    alert("11");
    break;
  case 12:
    alert("12");
    break;
  default:
    alert("其他");
}

```

例子2：[演示地址](http://codepen.io/zhaojianxin/pen/KgRyrP)

```
i=10
switch(i){
  case 10:
    alert("10");
          //这里没有break，即使满足条件也会继续往后走
  case 11:
    alert("10或者11");
    break;
  case 12:
    alert("12");
    break;
  default:
    alert("其他");
}

```
思考一下为什么例子1中只有一个弹窗，而例2中会弹出两个？


##return 是函数返回语句，返回的同时也将函数停止。体会下面的例子

[演示地址](http://codepen.io/zhaojianxin/pen/qaYVRX?editors=0011#0)
```
function test(){
  for(var i=0;i<10;i++){
    if(i==5) return;
    console.log(i);
  }
}
test();

```
