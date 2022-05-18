- 含义
	- 它允许一个函数返回的可遍历对象生成多个值
	- 返回的值为一个迭代器对象
- 例子
	- 在使用中你会看到\*语法和一个新的关键字yield
	```JS
	function *infiniteNumbers() {
	  var n = 1;
	  while (true){
	    yield n++;
	  }
	}
	 
	var numbers = infiniteNumbers(); // returns an iterable object
	 
	numbers.next(); // { value: 1, done: false }
	numbers.next(); // { value: 2, done: false }
	numbers.next(); // { value: 3, done: false }
	```