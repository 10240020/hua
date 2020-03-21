内存泄漏：
    任何对象在您不在拥有或需要它之后依然存在,在垃圾回收站定期扫描对象,并计算引用了没个对象的其他对象的数量,如果一个对象的引用数量为0(没有其他对象引用过该对象)对该对象的唯一引用是循环的,那么该对象的内存即可回收,setTimeout的第一个参数使用字符串而非函数,会引发内存泄漏闭包、控制台日志、循环(在两个对象彼此引用保留时)就会产生一个循环

执行上下文
[[scope]]:每个javascript函数都是一个对象,对象中有些属性我们可以访问,有些属性我们访问不了,这些属性仅供javascript引擎进行使用,[[scope]]其中一个
[[scope]]指作用域,其中储存了运行期执行上下文的集合.
作用域链:[[scope]]中所储存的执行期上下文对象的集合,这个集合呈链式链接,这种链接叫做作用域链

运行期上下文
当函数执行时,会创建一个执行期上下文的内部对象.一个执行期上下文定义一个函数执行时的环境,函数每次执行时对应的执行上下文都是独一无二的(每一个上下文代表每一个函数执行)多次调用一个函数会导致创建多个执行上下文,当函数执行完毕,立马会进行自我销毁
查找变量
从作用域顶端往下一次向下查找

function add(){fucntion b(){}}
add------>GO(全局window)
b------>AO(自身定义AO)
        GO

对象包装
    对象创建
    var obj = {} plainObject 对象字面量/对象直接量
    构造函数
        系统自带的函数构造 new Objcet()
        自定义函数构造
        形参实参可以进行定义调用
        function dmeo(color){this.color=color}
Objcet.crate(原型)方法

构造函数三段式
函数体前面加隐式的this = {}
执行this.xxx = xxx
隐式返回this

包装类
new string();
new boolean();
new number();
数字的对象能参与运算,一旦参与运算就彻底变成纯数字这不是对象里的数值  
数字有原始值数字和对象数字---原始值不能有属性和方法----对象有属性和方法
typeof()返回属性值类型  number string boolean undefined funcion Object等

原型
原型是function对象的一个属性,它定义了构造函数制造出对象的父级.通过该构造函数产生的对象,可以继承父级的属性.原型也是
利用原型特点和概念,可以提取出共有属性
对象查看原型->隐式属性_proto_
对象查看构造函数-constructor
person.prototype = {}---原型对象
构造函数对象里的属性不能更改原型对象上的属性person.prototyoe
继承

原型链 
大多数对象的终端都会继承Objcet.prototype
Objcet.protoype{}是最终原型
Objcet.create(原型)----Objcet.create()里面放原型----create是访问原型
this指向是,谁调用这个方法,this便指向谁
null和undefined无法调用tostring
call()----call让某个函数或方法调用某一个特定的原型
apply()-----必须传数组并只能传一个函数
call()和apply()传参列表不同---改变this指向

重写---javascript自身重写的六种方法
Objcet.prototype.toString()
number.prototype.toString()
Aarry.prototypr.toString()
boolaen.prototype.toString()
string.prototype.toString()

Math.floor(向上取整)和Math.ceil(向下取整)Math.random(产生随机数)
可正常计算的范围 小数点前16位，后16位

属性私有化变量
只有属性自身进行调用,外部访问变量,访问不了
