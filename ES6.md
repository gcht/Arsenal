# ES6 循环引用
* 代码
```
// a.js如下
import {bar} from './b.js';
console.log('a.js');
console.log(bar);
export let foo = 'foo';

// b.js
import {foo} from './a.js';
console.log('b.js');
console.log(foo);
export let bar = 'bar';
```
* 结果如下：    
b.js    
undefined    
a.js    
bar    
> 上面代码中，由于a.js的第一行是加载b.js，所以先执行的是b.js。而b.js的第一行又是加载a.js，这时由于a.js已经开始执行了，所以不会重复执行，而是继续往下执行b.js，所以第一行输出的是b.js。接着，b.js要打印变量foo，这时a.js还没执行完，取不到foo的值，导致打印出来undifined。b.js执行完，开始执行a.js，这时就一切正常了。

