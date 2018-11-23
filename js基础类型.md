# 数组 map
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>点击按钮将数组中的每个元素乘于输入框指定的值，并返回新数组。</p>
<p>最小年龄: <input type="number" id="multiplyWith" value="10"></p>
<button onclick="myFunction()">点我</button>
<p>老数组: <span id="demo"></span></p>
<p>新数组: <span id="demo2"></span></p>
<script>
var numbers = [65, 44, 12, 4];
function multiplyArrayElement(item, i, array) {	
	//item是数组item i是索引，array是原数组
	alert('map遍历中，一个'+arguments.length+'个参数\n'
		  +'第1个：'+item +'\n'
		   +'第2个：'+i +'\n'
		   +'第3个：'+array +'\n'
	);
    return item * document.getElementById("multiplyWith").value;
}
function myFunction() {
	var numbers2 = numbers.map(multiplyArrayElement);
    demo.innerHTML = numbers;
	demo2.innerHTML = numbers2;	
	
    alert('原属组:'+numbers.toString())
	alert('新属组:'+numbers2.toString())

}
</script>

</body>
</html>
```
