
*运行js的两种方试
	 *浏览器
	 *nodejs
*js调试
	*window.alert;
	*console.log;
*如何调试
	*bug:程序中的一切错误；
	*debug:发现错误，解决错误；
	*js程序出错 -->f12--——>console
		*console: 错误信息：3 部分
			错误类型：错误原因  **出错位置的连接**
		*出错的现象：出错的位置桶<script>的程序：
			出错前的程序正常执行
			出错位置及其之后的程序不受影响
			其他<script>不受影响；
**js变量：
 		*what:内存中存储一个数据的存储空间，再起个名；
 		*when:程序中的数据都要用变量保存，再处理
 		*how :声明  赋值 取值
 			*声明：内存中创建一个新的变量
 				how: var 变量名；
 			*赋值： 将一个数据存入变量中
 			 	how: 变量名=值；
 			*取值： 从变量中取出数据；
 				how:使用变量名就是使用变量值；
 			“，”优先级低于等号；
 		*变量命名：
 			*不能用数字；
 			*不能用保留字关键字
 			*  **见名知义**
 			*  **驼峰命名
 		***特殊情况
 			*为未声明的变量赋值-->js自动创建同名变量在保存数居
 			*尝试从未声明的变量取值——> 会出错 not definde
 			*变量仅声明未赋值在内存中值未undefined; 
 			*对已有的变量赋新值会覆盖旧值
 		****声明提前;程序正式执行前，会将var 声明的变量提前 赋值留在原地；
 				遇见声明提前的问题，多要先声明，在判断输出；
 				example:
 					console.log(a);//undefine
 					var a=100;
 					console.log(a);//100
 					var a=200;
 					console.log(a);//200
 					console.log(b)//error
 					b=100;
 					console.log(b)//100
**常量：一旦声明值不可改变；
 		*when :只要创建不可擅自改变时；
 				example:PI G
 		*how :const 常量名 = 值；
 		*常量名要大写
 		***强行给常量修改值不会起作用
***数据类型
	*what:内存中存储不同数据的存储格式；
	***js数据类型分为两大类：***原始类型  ***引用类型
	***原始类型：值保存在本地的数据类型
		*五种
		*Number 专门保存数字的类型
		*String 专门保存字符串的类型
		*Boolean 专门保存真假的类型
		*undefined 只有一个值 undefined
		*null 表示不指向任何的地址
		***************************************
		*Number 专门保存数字的类型 不加引号
			*when：要参与算数计算或比较大小
				身份证，银行卡号等不用 Number 类型
			*所占空间：64位二进制数保存的 64bit = 8bytes
				n.toString(2) ;转为2进制数；不论多大的数字所占的空间是一样的都是8字节（bystes）;
			****舍入误差：计算机无法精确到 1/10
						example:
							var total= 1.6;
							var money=2.0;
							var b=money-total;
							console.log(b)//0.3999999999999999 
							console.log(b.toFixed(2));//***.toFixed(2);2表示两位小数
		*String 专门保存字符串的类型  加""
			*when:保存文字 或 斤用于显示的数字时
			*所占空间 ： js程序内存中的字符都是用unicode标识的
				unicode: 对全球主要语言每一位字编一个号
					查询unicode 
						str.charCodeAt(0); //转化为unicode编码
						str.toString(2)//转化为二进制
				内存中每个英文字母、标点占一字节，每个汉字占2个字节
				****字符串一旦创建不可改变；
				"+"如果参与字符串运算自动转化为字符拼接；
					example
						var str  = "hello" + "world";
						创建过几个字符串： 3个
		*Boolean false/true;
		*undefined   
		*null   
		***程序中的变量和数据库中的差距
			变量是内存中的  数据库是硬盘上的文件
			临时的		   持久的
			客户端          服务器只保存一份
		****************************
	   ***数据类型转换
			***js弱类型语言
				1，声明变量时不用规定存储的带护具类型
				2， 赋值时，动态决定变量存储的数据类型
				3，运算时js动态转换数据类型
			***两类：
				隐式转换：js自己完成
				强制转换：程序员自己调动
				**隐式转换
				 算术计算中,一切类型自动转为 Number 类型
				 隐式转换，仅影响表达式的结果不影响变量中存储的值
				 	"2"——>2  true/false -->1/0
				 	特例："+"只要有一方为字符串则自动转为字符串拼接
				 		  "-"不遵守这个法则
				 	example 
				 		var n1 = 2, n2 = 3;
				 		var s1 = "2", s2 = "3";
				 		var b1 = true,b2 = false;

				 		console.log(n1+n2);//5
				 		console.log(n1+s2);//23
				 		console.log(b1+s2);//"true"+"3"true3
				 		console.log(s1-b1);//"2"- true(1)=1***1***
				 		console.log(s1*b1);//2*1=2
				 		console.log(s1/b2);//Infinity
				 		console.log(s2-n2);//3-3=0***0***
				 		console.log(b1+s1-n1);//NaN 俩俩计算
				 	 NaN not a  number说明运算中包含了无法转换为数字的值不是数字的数字
				 	typeof(NaN):number 
				 	NaN 与任何数据计算都是 NaN
				 	typeof(x)用于判断x的数据类型
				   **表达式：有数据和运算符组成的一个公式
				          默认从左向右两两计算
				**强制转换：主动控制，调用专门的函数执行转换；
					1.任意类型 to string:2种；
					 var x = x.toString();
						任何对象都有toString方法；
					 var str = string(x)-->隐式转换的原型；
					2. 任意类型 to Nunber:2种；
					  var n = Number(x);-->隐式转换；//x必须为纯数字
					  var n = parseInt(str);//str是string 如果不是字符串js就会自动转为字符串
					  var n = parseFloat(str);
					      parseInt()原理：从str开始位置逐个读取每个字符直到碰到第一个不是数字的字符时，停止读取。自动忽略开始碰到的空格
					      parseFloat()原理：只认第一小数点；
					      Number() vs parseInt()
					      Number(true) -->1;
					      parseInt(true)-->parseInt(string(true))--NaN

					      example 
					         var width =  "12px";
					         parseInt(width)-->12;
					         parseInt("we34ju")-->NaN;
					3. 任意类型 -->Boolean: var  bool -->Boolean(x)-->隐式转换
						false : "" NaN undefined null 0 
						其余都是true
			   ******反是从用户获得都是string
	   ***运算符和表达式
			*程序：让计算机按照人的想法执行任务
			*运算符：就是程序中模拟人的思维运算或判断的符号
		  	 	*算数运算符：+  -  *  /  %/;
		  	 	  %运算：余数运算
		  	 	    %how:判断奇偶数
		  	 	    %how:确保运算结果不超过某个最大值（就是除数）；
		  	  		++/--:将当前变量中的值递增递减1
		  			when : 只要是对变量中的值的增递减1时用
		  			how  ；
		  		   ++/--单独使用前后都一样
		  		   参与到*其他表达式中*
		  		   ++n，将n中的值+1，然后返回*新值*$先++后运算$
		  		   n++, 将n中的值+1, 然后返回*旧值*$先运算后++$
		  		    example
		  		       var n = 3;
		  		       console.log(n++)//3
		  		       console.log(n);//4
		  		       console.log(++n);//5
		  		       console.log(n);//5
		  		       var m = 2;
		  		       var r = m++ + ++m + m++;
		  		       			2 m=3  4m=4  4m=5  r=10;
		  		       console.log(r);
		  		*关系运算符： 将两个值比较 ; > < >= <= == ===
		  		  * 返回true/false
		  		  **隐式转换：将所有类型转换为number在比较
		  		  **特殊情况：三种
		  		    *1，两个字符串比较：PK每一位unicode编号；
		  		      "3">"10"-->true
		  		    *2，***NaN 和任何数据做大小等于比较都返回false***
		  		        ***NaN 和任何数据做不等于比较永远返回true***
		  		        ****isNaN(x)专门判断是不是 NaN;
		  		        只要判断一个数值是否是数字或能被转为数字
		  		        ***Number("")会自动把空转为0
		  		         isNaN(Number("")); isNaN(Number(true));
		  		    *3，undefined null
		  		       Number(undefined) --> NaN
		  		       Number(null) --> 0
		  		        undefined == null // true  
		  		        undefined === null;
		  		       === 全等： 数据类型要相等 才比较值是否相等
		  		          不希望关系运算隐式转换时就用===
		  		       	******合理使用隐式转换******
		  		*逻辑运算：综合多个关系运算得出最终纠结伦
		  		  * && || ！ 隐式转换：自动将每个条件转为 boolean;
		  		     	 alert(4&&5);//5
						alert(4||5);//4
						alert(0||7);//7
						alert(9&&0);//0
						alert(0&&5);//0
 				  表达式1&&表达式2 12都是true才是true
 				  表达式1||表达式2  有一个是真就返回true
 				  ***********短路逻辑**************
 				   **example
 				      var n=10;
 				      var m=10
 				      var r = n++>10 || ++m>10;
 				      console.log(r);//true
 				      console.log(n);//11
 				      console.log(m);//11

 				      var n=10;
 				      var m=10
 				      var r = n++>10 && ++m>10;
 				      console.log(r);//false
 				      console.log(n);//11
 				      console.log(m);//10
 				    ******利用短路逻辑运算*******
 				      &&短路运用： 条件 &&（表达式）
 				       	**example 
 				       	   	var total = parseInt(prompt("请输入总价"));
 							total>=500&&(total*=0.8);
 							console.log(total);
 					  || 短路逻辑
 					      关系运算||（操作表达式）；
 						   	var input = prompt("qingshuru");
 							input!="" || (input = "主任什么都没留下");
 							console.log("恢复"+input);
 						*****如何判断是不是一个汉字
 						    第一个汉字为“一”————>unicode \u4300
 						    最后一个汉字"u9fa5";
 			    *位运算： >>   <<
 			       	n<<m  将n的二进制左移m位；
 			       	 example
 			       	     1<<3 ————> 1*2的三次方
 			       	n>>m  将n的二进制右移m位；
 			       	   example
 			       	      64>>3--> 64/2的三次方
 			    *扩展复制运算：+= -=  /= / *=
 			    *三目运算(三元运算) ： 根据不同的条件，多选一，返回不同的*结果*
 			       语法： 条件一?值1：
 			              条件二？值2：
 			                    ?	:
 			                    。。。:
 			                    默认值;
*****函数************************************************************
 	***函数		
 	    *函数： 封装了具有特定功能的代码段  声明 定义 调用
 	    *声明并且定义一个函数
 	         function 函数名([参数变量列表]){
 	         		函数语句；
 	         		[return];
 	         }
 	    *调用函数：[var 返回值 =]函数名([参数列表]);
 	      *函数只有调用时才会执行；
 	      *反复调用，反复执行；
 	      *一次修改处处生效
 	    *函数的参数：专门接受纯如函数内部的**变量**
 	       *如何定义函数参数 ：function函数名(变量1 ，变量2，。。。){}
 	       *参数赋值：函数名(变量1 ，变量2，。。。);
 	    *返回值：方法调用后，返回的执行结果！——一个数据；
 	         *通过return返回
 	         ********return 单独用 退出函数执行**********
 	         *******函数仅负责返回值，不负责保存返回值，必须var 变量 = 函数名();*****
	***变量作用域
	   *：一个变量的可用范围
	   *两种作用域：全局作用域，函数作用域
	   	  *全局作用域：一个变量可以再程序的任何位置被访问；
	   	  *函数作用域：一个变量尽在函数调用时，内部被访问；
  	   *两种变量：全局变量 局部变量
  	   	  *全局变量：定义在全局作用域中的变量；
  	   	  	 *1，直接在任何函数外生声明的变量
  	   	  	 	 全局变量都属于** window————全局对象**
  	   	  	 *******2，无论任何位置为从未声明过得变量赋值时自动创建全局变量***
  	   	  *局部变量：定义在函数作用于中的变量；
  	   	  	 *函数内部的var的变量；
  	   	  	 *参数变量
  	   	  *****函数内存 ： 函数其实引用类型的对象；函数名是只想函数对象的变量；
  	   	     函数调用时根据函数名的地址找到函数对象；
  	   	     函数调用完：
				*************************************
				example 01
				     var a=100;
 					 function fun(){
  						a++;
  						console.log(a);
 					 }
 					 fun(a); //101
 					 console.log(a);  //101
 				example 02
 	   ***声明提前：在程序执行前或函数被调用前，将 var 声明的变量和 function声明的函数提前到**当前作用域**的顶部集中创建 ；
 	   	  ****强调：仅声明提前*赋值留在原地
 	   	     example01;
 	   	      		fun1(){
 	   	      			console.log(1);
 	   	      		}
 	   	      		fun1();//2;//画内存图；
 	   	      		fun1(){
 	   	      			console.log(2)
 	   	      		}
 	   	      example02:
 	   	         var a= 100;
 	   	         function fun(){
 	   	         	console.log(a);//undefined;
 	   	         	var a=90;
 	   	         	console.log(a);//90
 	   	         }
 	   	         fun(); undefined 100;
 	   	         console.log(a); //100

 	   	           var a= 100;
 	   	         function fun(){
 	   	         	console.log(a);//100;
 	   	         	 a=90;
 	   	         	console.log(a);//90
 	   	         }
 	   	         fun(); 
 	   	         console.log(a); //90
 	   	       example03
 	   	          function foo(){
 	   	          		console.log(2);
 	   	          }
 	   	          foo();//2
 	   	          var foo=100;
 	   	          console.log(foo)///100
 	   	          foo();error;
 	   		function (){}会整体提前 ；var foo = function(){} 赋值还在原味
 	   ***按值传递： js中无论变量间赋值或使用变量传递参数时，都是将变量中的值复制一个副本给对方；
 	       example:
 	          function buy(what,card){
 	          	card-=5;
 	          	console.log("余额"+card);
 	          	return "香喷喷的"+what;
 	          }
 	          var card=10;
 	          buy("鱼香肉丝",card)； 余额5；
 	          console.log(card); //10；
 	   **全局函数：ES标准中已经定义好的，开发者可直接调用的函数
 	      *parseInt(s[, radix]),parseFloat;
 	      *isNaN(x);
 	      *decodeURI(uri);decodeURIComponent(s);encodeURI(uri);encodeURIComponent(s);
 	      *eval(code);
 	      *isFinite(n);//判断是不是有限的；返回true/false
 	      	*编码/解码
 	      	   *编码：将url中的非法字符，改为合法字符；url不容许出现多字节字符；
 	      	   		/s?word=%E5%BC%AO 张#utf-8编码#
 	      	   		解决：将url中的多字节变为单字节：
 	      	   		example01
 	      	   		   /*用户输入搜索关键字 程序价格关键字编码为单字节拼接成url*/
 	      	   		   var url ="http://www.baidu.com/s?word=";
 	      	   		   var input = prompt("baiduyixia");
 	      	   		   input = encodeURIComponent(input);
 	      	   		   alert("向服务器发送请求"+url+input);
 	      	   		   /*服务器解码*/
 	      	   		   alert(服务器解码后：+decodeURIComponent(input));
 	      	   *解码：将url中的非法字符编码后的内容恢复成原文
 	      	*eval(code):计算字符串格式的表达式的值或执行字符串格式的JS语句；
 	      				ajax转数据；
 	      				var input = "3*4+8+78";
 	      				alert(eval(input));//
 	      				var input="document.write('string');"
 	      				eval(input);会执行；
 	      **不是全局函数是DOM 不在ES标准中定义的alert(message);
 	      **不是全局函数是DOM 不在ES标准中定义的prompt(message[, default])
	****分支结构：顺序，分支，循环
 		************
 	   		顺序：程序默认从上往下执行;



 	   		分支：根据不同条件执行不同语句；
 	   		循环：反复执行，达到临界条件停止；
 	   		**********需求IPO********input process Output;
 	   	*******if结构：
 	   	  if(条件){
 	   	  	语句；
 	   	  }else if(条件){
 	   	  	语句；
 	   	  }else{语句}；
 	   	  example:找最大
 	   	     *******function getMax(a,b,c){
 	   	     	var max = a>b?a:b;
 	   	     	c>max&&(max=c);
 	   	     	return max;
 	   	     }
 	   	     /*注意类型转换*/
 	   	      console.log(getMax(parseInt(prompt("message")) ,parseInt(prompt("message")) ,parseInt(prompt("message")) ));
 	   	*******switch case  ******全等比较；*****
 	   	       switch(表达式){
 	   	       	case 值1:
 	   	       	  code1;
 	   	       	  break;//停止并跳出当前结构，并不是一定要有break;
 	   	       	case 值2：
 	   	       	   code2;
 	   	       	   break;
 	   	       	  default:
 	   	       	     代码段；	

 	   	       }
 	   	********循环：循环条件；
 	   			循环变量：循环条件中用于比较的变量；一般想着不满足循环条件的趋势变化
 	   			语法：var 循环变量 = 初值；
 	   				***while(循环条件){
 	   						循环体；
 	   						迭代循环变量；//也可以在前面；
 	   					}
 	   					退出循环：1自然退出 2手动循环 break;
 	   					example
 	   					   var input="";
 	   					   var a = 6;
 	   					   	while(input!=a){
 	   					   		input=parseInt( prompt("请输入1-9的整数"))；
 	   					    	alert(
 	   					    	input>a?"打了":
 	   					    	input<a?"笑了":"猜对了";
 	   					    	)	
 	   					   	}
 	   					example
 	   					  /*随机数的公式*/
 	   					  *****var n = parseInt(Math.random()*(max-min+1)+min);
 	   				***do{循环体；迭代循环变量循环}while(循环条件);
 		*********js没有块级作用域 只有全局和函数作用域*************************
 	    *******for循环：循环变量的变化规律固定就优先选择 for 循环；
 	    			求和：for(var i=1,sum=0; i<=100; sum+=i++);
 	    					console.log(sum);
 	   				倒数求和：for(var i=1,sum=0; i<999; sum+=1/i,i+=2);
							console.log(sum);
		*********for 循环要考虑循环次数；次数越少效率越高；
					continue:跳过；###可以用否定条件代替使用很少用；
		*********99乘法口诀表；
					!(function(){
						var str="";
						var x=1;
						for(var l=1; l<=9; l++){
							for(var i =1; i<=l; i++){
							x=i*l;
	  						str += i+'*'+l+'='+x+(x<10?"   ":" ");
							}	
							console.log(str);
							str="";
						}
	
					})();
		*********输出正三角：
						!(function(){
								function printTriang(x){
									var str="";
									for(var l=1; l<x; l++){
										for(var i=1; i<l; i++){
												str += "*"					
										}
										console.log(str);
										str="";
										}
									}
							printTriang(6);	
						})();
						2:
						(function(){
							function printTriang(l){
								for(var i=0,str="*";i<l;str+="*",i++){
							 	console.log(str);
							 }
							}							 
						})()
						******
						    function printTriang(l){
						    	for(var r=1; r<=l; r++){
						    		for(var i=0,str="";i<1; i++){
						    			str+=i<(l-r)?" ":"*"
						    		}
						    	}
						    		
						    }	
	**********程序就是数据结构+算法
				好的数据结构可提高程序执行的效率；
*****数组******************************************************************
	*******数组：一组连续的变量组成的集合————统一起一个名字；
				批量管理多个数据；
	*******数组内存：数组是引用类型对象；
				数组不是直接保存在window而是把内存地址保存在window中
				通过数组名寻找对象；

		****创建  赋值  取值
			**创建：4种
				1.***常用 var 变量名 = [];————>创建一个空的数组对象；
				2.***常用 var 变量名 = [值1，值2，值3,.....];————>创建数组并初始化元素；
				3.**不常用 var arr = new Array()——>创建一个空数组对象；
							new 创建一个新对象；并返回新地址保存在变量值；
				4.**不常用 var arr=new Array(n);
			**使用数组：使用变量等效使用数组；
					数组对象中，每个元素都有一个下标；
					数组变量[i]————>获取i位置的元素的值
					数组变量[i]的用法与普通变量完全一样；
			**赋值：数组变量[i]= 新值；
			**取值：数组变量[i]= 新值；
			**var my = ["报"，"报"，"报"，"报"，"报","报"，"报"]
				var lp = my;
				my = null;释放了my的内存地址 此时lp还在引用数组，数组还从在，
				    如果lp=null 则释放数组，垃圾回收器回收；
			***垃圾回收器： 专门释放对象内存的一个程序；
							在底层，后台，伴随当前程序同事运行；
							引擎会定时调用垃圾回收期；
							只有当一个对象不被任何一个人引用时；
			****js位不存在的位置赋值，不会出错；会自定赋值；
			****从不存在的位置取值不会出错，也不会增加新元素；而是返回undefined;
			******example;
				var  emps=[];
				var input = "";
				while((input = prompt("请输入员工姓名"))!="exit"){
	 				/*赋值表达式的结果是等号右边的值*/
	
					emps[emps.length]=input;
	
				}
					console.log(emps);
			****数组是对象：封装了一组数据，并提供了对数组的操作方法；
				.length的属性，获取数组中的元素个数 ！= 实际元素个数(当为不存在的位置赋值时，直接给到100的时候就不是了)；
				何时使用：arr[arr.length-1]:获取任意长度数组的最后一个元素；
						 arr[arr.length]=新值；数组末尾追加新元素；
						 改小arr.length的值，可删除末尾元素；
				数组遍历：从下表0开始，依次取出每个元素，反复执行相同的操作；
					*******example:
						function getMax(arr){
	 						for(var i=1,max = arr[0]; i<arr.length; arr[i]>max&&(max=arr[i]),i++);
							return max;
						}
					*******example:
						function indexof(arr,name){
							for( var i=0; i<emps.length; i++){
								if(emps[i]==name){
									return i;
								}
							}
							return -1;
						}
				关联数组：可以自己定义下表名称的数组；
					创建关联数组：var fbb = [];fbb["sname"]="范冰冰"；fbb["math"]	= 78;
					访问关联数组：自定义的下标名；
					关联数组中.length属性失效；
					关联数组（hash）:下标不重复的；
						优势：利用hash算法，精确定位某个下标位置；不用遍历；
						hash内存：hash会通过hash算法根据下标随机分配地址（地址名随机）所以打印顺序是随机的；类似住酒店；循序不一样；
					遍历关联数组：for(var key in arr){
						key;/*key为下标号*/
						key为当前元素的下标；arr[key]为值；
					}
					*****/*去除数组中重复的元素：*/
 						var arr = [1,2,4,5,2,4,5,2,7,9,34,234,3];
						var hash = [];
							for(var i=0; i<arr.length; i++){
						hash[arr[i].toString()] = 1;
							}
							console.log(hash);
			*****API：应用程序变成接口
			****数组API:
				*****arr to String;
					 var str = arr.toString();
					 var str =  arr.join("separator");
				*****优化： 问题：频繁字符串拼接造成内存浪费；
					解决：先将要拼接的字符串放入数组，
					最后 arr.join("");
					******用数组实现三角形；
						for(var i=0 arr= [];; i<7; i++){
							for (var j=0; j<i; j++)
								{arr[arr.length]= "*";}
								console.log(arr.join(""))
							

							}
					****打印反三角：
						for(var i =0; i<=7; i++){
							for(var j=0,arr=[]; j<i; j++){
								arr[arr.length]= i<7-i?" ":"*";
							}
							console.log(arr.join(""));
						}
					****乘法口诀表：
							for(var i=1; i<=9; i++){	
								for (var j=1,arr=[]; j<=i; j++){
									arr[arr.length] =[j,"x",i,"=",j*i,""].join("");
								}
								console.log(arr.join(" "))
							}
					***
				*****拼接和截取：元对象保持不变，返回新对象；
				     var newArr = arr.concat(新值1，另一个数组，新值2.......)
				     var subArr = arr.slice(start[, endi+1]);含头不含尾；
				     			第二个参数可以省略，省略可以取到最后；
								两个参数都可以去负数，则从后面往前取；		     			
				*****arr.splice(start[, deleteCount][, values]):删除 插入 替换
				*****arr.reverse()；
				*******数组排序arr.sort()———>以字符串排序；
					 比较器函数：专门比较任意两数大小的函数；
					 		两个参数分别表示要比较的任意两值；
					 		无论比较逻辑是什么，都要返回一个数字；
					 ***arr.sort(compareNum——>比较器函数)；拍数字；
					 	颠倒比较器的结果的正负return -(a-b)可变为降序；					 	example
					 		var arr=[11,3,5,17,8,32,12,23,56];
							var strs = ["sad","dasf","2213342","dasf","34"];
							
							function compareNum(a,b){
								return a-b;
							}
							arr.sort(compareNum);console.log(arr);
							strs.sort(strs,compareStr);console.log(strs);
				******函数对象作为参数；
						函数名后面加()，表示立即执行；
						函数作为对象传递时，仅适用函数名，不加（）；
						比较器函数bubble()：
							var arr=[11,3,5,17,8,32,12,23,56];
							var strs = ["sad","dasf","2213342","dasf","34"];
							function bubble(arr,compare){
									for(var n=1; n<arr.length; n++){
										for(var i=0; i<arr.length-n; i++){
											if (compare(arr[i],arr[i+1])>0) {
												var tmp = arr[i];
												arr[i] = arr[i+1];
												arr[i+1] = tmp;
											}
										}
									}
							}
							function compareNum(a,b){
								return a-b;
							}
							function compareStr(a,b){
								return a>b?1:
										a<b?-1:0;
							}
							bubble(arr,compareNum);console.log(arr);
							bubble(strs,compareStr);console.log(strs);
				******冒泡排序:判断是不是交换位置
						for(var n=1; n<arr.length; n++){
							for(var i=0; i<arr.length-n; i++){
								if (arr[i]>arr[i+1]) {
									var tmp = arr[i];
									arr[i] = arr[i+1];
									arr[i+1] = tmp;
								}
							}
						}
				******冒泡排序
				*****栈和队列：js中没有真正的栈和队列的类型；一切都是用数组对象模拟的；		
					栈：只能从一端进出的数组，另一端封闭：
							以后只希望数组只能从一端进出时；
					末尾出入栈；已经入栈元素下标不变
						***push***入栈：arr.push(values);
						***pop**出栈：var last = arr.pop();
					开头出入栈：每次入栈新元素时；以入栈的元素的位置会向后移；
						***sunhift**入栈： arr.unshift(values);
						***shift()**出栈： var first = arr.shift();
					*******arr.length会变化故循环时用while(){};
					****入栈出栈模拟十进制转二进制算法
							function dec2bin(num){
								var arr=[];
								while(num>0){
									  arr.unshift(num%2);
									  num = parseInt(num/2);
							
							
								}
								return arr.join("");
							}
					队列：只能从末尾进入数组，必须从开头出数组；
					**结尾入列push; 开头出队列：var first = arr.shift();
			***二维数组：数组中的元素又引入另外一个子数组对象；***保存横行数列***上下级关系			
				***创建二维数组：
					1先创建在在赋值；var  arr=[]; arr[0]=["石家庄","baoding",""]; arr[1]=["",""]
					2创建数组时同时初始化数组；
						var data = [
							[0,1,3,4,4],
							[234,2,3,4,5,56,5],

						]
				***二维数组内存图：31.jpg
				***访问二维数组中的数据：arr[行下标][列下标]；行下标不能越界；越界则为undefined,undefined不是数组所以就不能访问列；
				***遍历二维数组；外层循环遍历行，内层循环遍历列；
*****字符串*****************************************************	
	***：多个字符组成的一个*只读*的集合（数组）
	***：凡是数组对象中，不修改原对象的API,字符串都能用；
			slice indexOf;
		 凡是数组对象中，修改原对象的API,字符串都bu能用:push sort splice;
	***String API: 所有API不可能直接修改原字符串；
		**转义字符："\"" "\\" \n 换行  \t Tab;
		**大小写转换；转大写：str.toUpperCase();转小写：str.toLowerCase();
				var input="";
				while( (input=prompt("输入验证码"+code).toLowerCase())!=code.toLowerCase()){
					alert("shurucuowu ");
				
				}
		**获取制定位置字符（同数组） 
			1 str[i] 也可srt[str.length-2];
			2 str.charAt(n)
			3 str.charCodeAt(i);-->返回unicode号；
		**任何东西加""会转为字符串；
		***查找关键字的位置 
			var i = str.indexOf("kword"[,stari]);如果找不到返回-1;
			var i = str.lastIndexOf(targetElement[, startIndex]);
			查找敏感词的函数：
				function findKwords(input){
					var index = -1;
					while((index = input.indexOf(kword,index+1))!=-1){
				
						alert("在"+index+"发现敏感词");
					}
				}
		***获取子字符串：var substr=str.slice(start, end); 含头不含尾
						var substr = str.substring(from[, to]);不支持负数；
						var subStr = str.substr(stari,取几个)；
						解码
						function decode(code){
							for(var i=0, arr=[]; i<code.length; i+=5){
								arr.push(String.fromCharCode(code,substr(i,5)));
							}
							return arr.join("");
						}
						获取域名
						function mail(emil){
							var index = emil.indexOf("@");
							
							var username = emil.slice(0, index);
							var domain = emil.slice(index+1);


							alert("username:"+username+"   domain:"+domain)
						}
		***切割字符串：var arr = str.split(delimiter[, limit]);arr中以数组方式保存字符串；
			**只要分段处理字符串时就要线分割在遍历；
			**固定套路 ：将字符串切割为字符数组：var chars = str.split("")//空字符创相当于把字符切割；
			***首字母大写
				function parseFirst(str){
					var arr = str.split(" ");
					for(var i=0; i<arr.length; i++){
						arr[i] = arr[i].slice(0, 1).toUpperCase()+arr[i].slice(1);
					}
					return arr.join(" ");
				}
			***颠倒字符串的位置
				function reverse(str){
						return  str.split("").reverse().join("");
				}
			***打印兵种
				function printRoles(str){
					 var arr=str.split("#");
					 for(var i=0; i<arr.length; i++){
					 	 document.write(arr[i].split("@").join(" ")+"<br>");
					 }
					
				}
				printRoles("tom@补给兵@60#marry@医护兵@89#Join@特种兵@30");
			***利用hash算法查询字符串出现的次数****也可以用正则匹配match*****
				var str = "helloeeoeee";
				function count(str,a){
					var arr = str.split("");
					var hash = [];
					hash[a]=0;
					for(var i=0; i<arr.length; i++){
						if(arr[i]==a){
							hash[a]++;
						}
						
					}
					console.log(a+"出现了"+hash[a]+"ci");
				}
				count(str,"o");
		***模式匹配：按照规则查找或替换字符串中的字内容；
			**查找： var i=str.search(/kword/i)*正则匹配i-->ignore:忽略大小写*;只能从开始位置找到第一个匹配的元素
				仅判断有没有关键字时使用；
				search专门用于模式匹配；
			***获得所有关键字的内容或个数：var arr = str.match(/kword/ig)-->g为全部匹配;  arr中保存了所有关键字的数组；
				如果没找到返回null;
				*match*只可以获取第一个关键字的位置；arr.index(只有不加g)才有效;
			*****替换：var newString = str.replace(模式，"替换内容");
					var newString = str.replace(/kword/ig,"替换的内容")；
					var kword  = /no/ig;
					function replace(input,kword){
						var arr = input.match(kword);
						input = input.replace(kword,"yes");
						console.log("替换了"+(arr?arr.length:0)+"出");
						console.log(input);
					}
					replace("no zuo no die",kword);
			*****
		***正则表达式RegExp：专门规定字符串中字符格式规则的表达式；
				****只要定义字符串格式柜子都用正则表达式
				****[]备选字符集：规定某一位字符可选的备选文字列表；
					****[备选字符列表]无论备选字符集中有多少字符，都必须且只能选一个；
					一个[]只代表以为字符；
					^排除；[^47]除了47都行；
				**** - 如果备选字符集连续可用-表示到；[0-9][a-zA-Z][一-十]
				****预定义字符集：专门表示常用的连续字符集；
					\d==>[0-9]一位数字；
					\w==>[0-9a-zA-Z_]:一位数字字母或下划线；
					\s==>[空字符]；代表一位空字符；空格 tab;
					.==>除了换行外，其他所有字符；
					\D \W \S 除了\d \w \s 的字符集；
				****量词：规定字符集出现的次数；
					明确数量的量词 {min,max} \d{6,8};
								  {min,} 至少；
								  {n}必须n位；
					不确定数量两次 ? ==>{0,1}可有可无，最多一次；身份证号 \d{15}(\d{2}[0-9xX])?
								  * ==>可有可无数量不限；
								  + ==>{1,}:至少出现一次；数量不限；
						    手机号正则验证：(\+86)?\s*[1][34578]\d{9}
								  如果冲突就用\转义；
		***RegExp 对象：封装了正则表达式，提供里利用正则表达式执行验证和查找的API;
			*创建 var reg = /正则表达式/ig；正则表达式在运行时不会改变；
				 var  reg = new RegExp("正则表达式","ig");
				 		var str1 = "\\d{6}";var reg new RegExp(str1,"ig")
				 		\\注意字符串转义；
			*使用：  
				格式验证：var bool = reg.text(str);返回 true false;
				*验证：从头到尾必须完整匹配；
				*test方法默认只要部分匹配就可；
					*解决：都要在正则表达式前加^,后加$:^表示必须以***开始$：表示必须以****结束；^$；表示必须完整匹配；
					*****密码验证 
					var reg = /^(?![a-z0-9]*$)(?![a-zA-Z]*$)[a-zA-Z0-9]{6,8}$/;
					while(!reg.test(prompt("输入密码"))){
						alert("格式不服 n 密码6-8位至少一位大写字母，至少包含一位数字");
					}					
					alert("message");
				**查找API：reg.exec(string)：在string中查找符合reg规定的关键字；
					****及查找内容有查找位置时只能arr=reg.exec(string);一个一个找不能保存需及时手动保存；
					**要加g;
					**var arr=reg.exec(string);
						arr[0]保存了当前关键字的内容；
						arr.index保存了当前关键字的位置；
						reg.lastIndex为下次查找开始位置
						exec(string)没找到会返回null;
						example:
							var str = "明明喜欢我，却不告诉我，别理我，我想静静；静静是谁？你先告诉我明明是谁";
							var reg = /明明|静静/g;
							var arr=null;
							while((arr=reg.exec(str))!=null){
								console.log("zai"+arr.index+"发现关键字："+arr[0]);
								console.log(reg.lastIndex);
							}
					****所有查找：在最合适的时候使用最合适的方法；
						1.var i= str.search(reg)-->判断有没有（不能制定开始位置；
						2.var arr = str.match(reg)-->获得所有关键字内容和个数.length；
							不能查找位置；
						3.var i = str.indexOf("kword"[,starti]);-->从指定位置开始，查找下一个关键字的位置； ***但是不支持正则；
						4.var arr  = reg.exec(str)即可以获得内容也可以获得位置，缺点复杂；
					***正则贪婪模式和懒惰模式：
						***默认贪婪模式：默认总是匹配最的字符串；
							原因：.* .+引起的
						***懒惰模式：仅匹配最短的符合条件的字符串；
							贪婪-->懒惰； .* --> .*?
					***取出html中的a	/<a\s+(.*?)href\s*=\s*['"]([^'"])*['"]/g
						从正则表达式中：用（）包裹要获取字内容的部分；
						程序中，本次查找后：RegExp.$n (n为第几个括号从1开始)；取出*本次*匹配结果中第n个（）匹配的字内容；
							正则中n从1开始；
					***去空格； ltrim()
						function ltrim(str){						 
							return str.replace(/^\s+/,"");
						}
						function rtrim(str){					 
							return str.replace(/\s+$/,"");
						}
						function trim(str){						 
							return str.replace(/^\s+|\s+$/g,"");
						}
			******string的正则API relace()  split(delimiter[, limit]);
				******var str = "纪委负责对全国党员干部的纪检监察工作";
					var reg = /纪[检委](监察)?/;
					var count = 0;
					var arr=null;
					while((arr=str.match(reg))!=null){
						str = str.replace(reg,arr[0].length==2?"**":"*");
					}
					console.log(str);
				******利用replace格式化数据
					"替换值"中，也可以使用$n，和RegExp.$n的用法完全相同；
							/*格式化身份证号的生日*/
						var pid = "130645198709173087";
						var birth = pid.slice(6,-4);
						var reg = /(\d{4})(\d{2})(\d{2})/;
							birth = birth.replace(reg,"$1年$2月$3日");
							console.log(birth);
						var time = "20171010124455";
						var reg1= /(\d{4})(\d{2})(\d{2})(\d{2})(\d{2})(\d{2})/;
						console.log(time.replace(reg1,"$1年$2月$3日$4点$5分$6秒"));
				*****切割  var arr= str.split(reg);
						var lis = "<li>tom</li>\n\t<li>lli</li>\n\t<li>tom</li><li>tom</li><li>tom</li>";
							lis = lis.slice(4,-5);
						var reg = /<\/li>\s*<li>/;
						var arr = lis.split(reg);
						console.log(arr);
							var html=arr.sort().join("</li><li>");
							document.write("<ul><li>"+html+"</li><ul>");
********Math******************************************************
	Math不能new：专门执行数学计算的对象；封装了数学计算中的常量
	1.取整: 上取整Math.ceil(x)  下取整Math.floor(x)  四舍五入取整Math.round(x)
		***Math.round()属于Math对象；返回值为数字
		***toFixed()输入number可以按任意小数位数取整；返回值为字符串类型
		*****保留任意小数
			function round(num,d){		
				return Math.round(num*Math.pow(10,d))/Math.pow(10,d);
			}
			*******console.log(round(555.555,2));//555.55;舍入误差；多计算几位可以避免舍入误差；
	2.乘方开方
		乘方：Math.pow(n,m);计算n的m次方
		开平方：Math.sqrt(x):计算x的平方根；
	3.获取最大值/最小值
		Math.max(args);
		Math.min(args);
	************固定套路：Math.max.apply(Math,arr);
	4. 随机数 Math.random() 0<=n<1的随机数；
		任意min到max之间取一个随机整数；
		********parseInt( Math.random()*(max-min+1)+min);
			Math.floor( Math.random()*(max-min+1)+min);
		********双色球案例
		*******生成4位随机验证码；
			var chars = [];
			for(var c=48; c<=57;chars.push(String.fromCharCode(c++)));
			for(var c=65; c<=90;chars.push(String.fromCharCode(c++)));
			for(var c=97; c<=122;chars.push(String.fromCharCode(c++)));
			function getCode(){
				var arr=[];
				for(var i=0; i<4; i++){
					arr.push(chars[parseInt( Math.random()*63)]);
				}
				return arr.join("");
			}
			console.log(getCode());
		******	验证码验证 function validCode() {
					var code = getCode();
					while((prompt("输入验证码"+code).toLowerCase())!==code.toLowerCase()){
							alert("message");
							code = getCode();
					}
					alert("验证成功");
				}
					validCode();
*****Date()***************************************************************
	****封装了时间点，提供了对时间和日期的操作的API
		1970年1月1日0点0分0秒至今的毫秒数；
	****创建Data对象；
		1. var now = new Date();创建一个新的日期对象，保存了*客户端*当前时间点的毫秒数；
		2. var time = new Date("xxxx/xx/xx [xx:xx:xx]");自定义时间对象；
		3. var time = new Date(年，月-1，日[,时，分，秒])；
		******日期对象可以相减 结果为毫秒差； 2 对任意分量做加减：Date对象
		******Date.getTime()获取时间；
		4.  复制日期对象
		    var date1 = new Date();
		    var date2 = new Date(date.getTime());
		*********example日期的计算；
				var hiredate = new Date("2012/6/30");
				var enddate = new Date(hiredate.getTime());
				enddate.setFullYear(enddate.getFullYear()+3);
				/*计算续签的时间*/
				var renewvl = new Date(enddate.getTime());
				 renewvl.setMonth(renewvl.getMonth()-1);
				 if(renewvl.getDay()==6){
				 	renewvl.setDate(renewvl.getDate()-1);
				 }else if(renewvl.getDay()==0){
				 	renewvl.setDate(renewvl.getDate()-2);
				 }
				console.log(renewvl.toLocaleDateString());
				var remindDate = new Date(renewvl.getTime());
					remindDate.setDate(remindDate.getDate()-7);
				console.log(remindDate.toLocaleDateString());
		*********example计算工作日；
					/*计算工作日*/
					function getDueDate(days){
							var now = new Date();
							for(var i=0; i<days; i++){
								if(now.getDay()==5){
									now.setDate(now.getDate()+2);
								}else if(now.getDay()==6){
									now.setDate(now.getDate()+1)
								}
								now.setDate(now.getDate()+1);
							}
						return now;
					}
					console.log(getDueDate(10).toLocaleDateString());
		*********/*日期转换为字符串的函数  解决各大浏览器的兼容问题
				xxxx年xx月xx日 星期几  上午/下午 xx:xx:xx*/
				function formate(date){
					 	var arr=[];
					 	/*年*/
						arr.push(date.getFullYear());
						/*月*/
						var  m= date.getMonth()+1;
						m<10?m="0"+m:m;
						arr.push(m);
						/*日*/
						var d=date.getDate();
						arr.push(d<10?d="0"+d:d );
						/*week*/
						var week = ["日","一","二","三","四","五","六"];
						arr.push(week[date.getDay()]);
								/*上下午*/
						date.getHours()<12?arr.push("上午"):arr.push("下午");
						/*h*/
						var h = date.getHours();
						h>12&&(h-=12);
						arr.push(h<10?h="0"+h:h);
						/*m*/
						var min = date.getMinutes();
						arr.push(min<10?min="0"+min:min);
						/*s*/
						var s= date.getSeconds();
						arr.push(s<10?s="0"+s:s);
						/*拼接字符串*/
						var str = arr.join("");
							/*替换*/
						var reg = /(\d{4})(\d{2})(\d{2})([日一-六])([上下]午)(\d{2})(\d{2})(\d{2})/;
						return str.replace(reg,"$1年$2月$3日 星期$4 $5 $6:$7:$8"); 
				}
***异常/错误处理**********************
	error:导致程序无法继续执行的异常状态
	js中一旦发生错误就会自动创建Error类型对象
	6种
		SyntaxError 语法错误
		ReferenceError 引用错误 找不到变量或引用对象
		TypeError  类型错误  错误的使用了对象的方法
		RangeError 范围错误  参数超范围； toString(-1);
		EvalError  调用eval()函数错误；
		URLError   URL错误；
	错误处理： 在程序发生错误时，保证程序不退出或正常退出；
	如何错误处理： try Catch 
				try{
					可能出错误的代码
				}catch(err){
					仅在发生错误时才执行
					一旦发生错误 err 中就会自动存入Error对象；
					1.记录/显示发生错的信息；
					2.继续向调用者抛出异常；
				}[finally{
					无论对错一定执行的代码段：释放资源；
				}]
	何时需要定义错误处理？某段代码只要有可能出错，都要抱在try catch 
	优先使用if else 结构判断已经预知的可能出错的错误
	无法预知时采用try catch；
	用法：
		1.解决各大浏览器的兼容问题
		2.抛出自定义异常 throw new Error("自定义错误消息")
**********function**********************************************(){}*******	
	function对象：js中一切都是对象；函数也是对象；函数名其实是引用函数定义对象的变量；
	*******arguments对象：
		重载：程序中可以定义多个相同函数名不同参数列表的函数，调用者不必区分每个参数的函数
			执行时，程序根据不同的参数调用不同的方法；
		在js中没有重载；但是可以用arguments对象模拟重载
		arguments对象：函数对象内，自动创建的专门接受所有参数值的类数组对象；
		arguments[i]:获得传入的下标为I的参数值；
		arguments.length:获得传入参数的个数；
		即使定义了参数，arguments对象同样回收到所有的参数值；

		example:/* js模拟重载 */
		********function add(){
				for(var i=0,sum = 0; i<arguments.length;sum+=arguments[i],i++)
				return sum;
			};
			console.log(add(11,2,34,5));
	*****函数对象
		***创建函数对象：3中方式
			1.声明方式： *只有声明方式才会被提前**不仅函数名提前整个定义也会提前*：
				function 函数名(){};在调用前后无所谓：
			2.函数直接量：var 函数名 = function(){};**函数名变量声明提前*赋值留在原地；**
					必须写在调用之前；
			3.使用new 创建函数对象：
				var 函数名 = new Function("a","b",,,,,"函数体")必须加""；
		****内存中的函数对象*2.png****
			***函数在创建对象时：同时创建两个对象；
				函数对象：函数的定义；
				作用域链对象：保存了函数对象可用的变量位置（地址表格）这个地址默认第一项指向window；
			***调用函数时又会创建1个新对象：活动对象；
				活动对象：专门保存局部变量的对象 ；
				***在作用域对象中追加指向活动对象的引用；
			***调用后：
				***默认仅释放活动对象
				***作用域链对象中的活动对象引用出栈；
	*******匿名函数：没有命名的函数 天生用来节省空间的
			1.匿名函数自调：定义完函数立即执行；执行完立即释放；
				***只执行一次时使用；
				如何自调：(function(){})(参数值);
				匿名函数自调不提前
			2.匿名函数回调：将函数作为对象传递给另一个函数由另一个函数自主决定在需要时调用
				 arr.sort(function(a,b){return a-b;});
				 只要将一个函数对象传递给其他方法调用时；
				 example:比较器函数
				 	var arr =[2,3,5,6,7,8,778,42,34,3];
					arr.sort(function(a,b){return a-b;})
					
					console.log(arr);
					arr.sort(function(a,b){return b-a;})
	******闭包:词法表示包括不必计算的变量的函数，也就是说该函数能使用函数外定义的变量。
		**全局变量局部变量的缺点
			全局变量：容易全局污染；
			局部变量：无法共享：不能长久保留;
		闭包：即可全局共享又可以长久保留的变量，又不会被污染；
		****1.定义外层函数，封装被保存的局部变量；
		****2.定义内层函数，执行对外层函数局部变量的操作；
		****3.外层函数返回内层函数的对象；并且外层函数被调用时，结果被保存在全局变量中；
		****何时使用：反复使用局部变量又避免全局污染；
			function outer(){
				var n= 1;
			
				return function (){
					return	n++;
				}
			}
			var getNum1 = outer();
			console.log(getNum());1
				var n = 100;
			console.log(getNum());2
			console.log(getNum());3
			console.log(getNum());4
			console.log(getNum());5
			var getNum2 = outer();
			console.log(getNum2());1
				var n = 100;
			console.log(getNum2());2
			console.log(getNum2());3
			console.log(getNum2());4
			console.log(getNum2());5
		********闭包内存：笔记本闭包内存图*结合函数的内存图*两者联合起来一起看；
		****闭包的特点：
			1.嵌套函数
			2.内层函数操作了外层函数的局部变量
			3.外层函数将内层函数返回到外部，被全局变量保存住；
		******判断闭包函数执行结果：
			*******外层函数被调用几次就有几个受保护的局部变量副本；
			****来自一个闭包的函数被调用几次，受保护的局部变量就变化几次
			********
				function outer(){
					var arr=[];
					for(var i=0; i<3; i++){
						arr.push(function(){return i;});
					}
					return arr;
				}
				var getFuns = outer();
				console.log(getFuns[0]()); //3
				console.log(getFuns[1]()); //3
				console.log(getFuns[2]()); //3
*****面向对象************************************************************
面向对象：在程序中都是用一个对象来描述现实中一个工具的东西
	包含：封装了属性和方法的储存空间；
	*******创建自定义对象的三种方法;
		1. 直接量var obj = {"属性名1":值1，
					  "属性名2":值2,
					  "功能名1":function(){},
					  "功能名2":function(){},....};
			****访问对象中属性的两种方式：obj.属性名； obj.[属性名]；
			****判断对象是否含有某种属性和方法
				*1.hasOwnProperty("propname")找到返回true 否则返回 false;
				*2."属性名" in 对象 找到返回true 否则返回 false;
				*3.直接使用obj.属性名作为条件：arr.indexOf===undefined; 不包含，undefined --> false;包含，值或 function(){};
					何时省略===：判断方法是否存在时，可省略=== 如果属性值一定不是 null 0 "" NaN 也可省略；

				*强行给js中不存在的属性方法赋值会自动创建同名属性和方法；
				*（访问对象中不存在的属性）相当于访问数组中不存在的下标：不会出错返回undefined;
			***this*******如何在方法中访问当前对象自己
				*****this关键字：运行时，指代正在调用方法的对象就是.前的对象；
					this本质是window下唯一的一个指针，指向当前调用方法的对象；
				**如何在方法内，访问当前对象自己的属性：this.属性名；
				**this和定义在哪儿无关！仅和调用时使用的当前对象有关；
				***如果无主的调用或赋值，都默认this都是window;
				*********example
					var a=2;
					function fun(){
						console.log(this.a);
					}
					var o={a:3,fun:fun};
					var p = {a:4};
					o.fun();//3
					console.log(p.a);//4
					(p.fun=o.fun)();// 2
					/*p.fun=(o.fun的值)-->是地址**相当于(fun指针)()-->匿名函数自调 					故为2此时this指向window*/
					//4;/*赋值表达式的结果相当于等号右侧表达式***的值***（是值）*/
					p.fun();//4
			*****属性名和方法名可以不加"";但是在底层hash算法都加着"";
			js中一切都是对象!所有对象的底层都是hash数组；
			遍历对象所有的成员就相当于遍历hash中的每个元素；
					var hmm = {
					sname:"hanmeimei",
					age:11,
					intrSelf:function(){
						alert("message")
						}
					}
					for(var key in hmm){
						console.log(key+":"+hmm[key]);//此处hmm.key不行 	用“.”会把key当做变量；
					}
		2. var obj = new Object() 创建空对象
				obj.属性名 = "";
				obj.方法名 = function(){};
		
		3.利用构造函数*反复*创建*相同结构*的对象(工厂模式)；
			描述一类对象结构的特殊函数；
			2步 1.定义构造函数
					function 构造函数|类型名(属性参数1,....){
							this.属性名=属性参数1;
							//在当前正在创建的对象中创建一个属性名并赋值为属性参数的值
							this.方法名 = function(){
								....this.属性名.....
							};


					}
					构造函数名.prototype.方法名 = function(){};
				2.利用构造函数创建对象
					var obj = new 构造函数名|类型名(属性值1,........)
					new : 1.创建了一个空对象； new obj = {};
						  2.用空对象，调用构造函数；
						  	构造函数在空对象中添加属性和方法；
						  3.设置新对象的_proto_指向构造函数的prototype对象；
						  4.返回新对象的地址；
		4.Object.creat(父对象，{扩展属性的列表对象}); 
	*******面向对象三大特点：封装 继承 多态
		***封装：将描述统一东西的属性和方法，定义一个对象中；
		***继承：父对象中的属性和方法，子对象可直接使用；
		***多态：同一个对象，在不同情况下，呈现不同的状态:
			重写：子对象觉得父对象的成员不好用。可定义自己的
				子对象与父对象的同名属性； 
			重载；同一方法名，传入参数不同 ，执行的操作不同；
	*******继承：js中一切继承都是原型对象实现的！
				代码重用；节省空间
			1.直接继承对象：修改对象的_proto_
				1.仅修改一个对象的_proto_
				 Obiect.setProperty(子对象，父对象)；
				 2.通过修改构造函数的原型对象，实现批量修改后续子对象的继承关系；
				 	构造函数.prototype = 父对象；
				 	强调：仅影响之后创建的对象的继承关系；之前创建的对象依然继承旧的构造函数的prototype;
			2.仅继承结构：
				function 父类型构造函数(属性参数1，属性参数2，){
					this.属性1=属性参数1;
					this.属性2=属性参数2;

				}
				function 子类型构造函数(属性参数1，属性参数2，属性参数3){
					父类型构造函数.call(this,属性参数1，属性参数2);
					this.属性3=属性参数3;
				}
				var obj = new 子类型函数(值1,值2,值3){}
				function Flyer(sname,speed){
					this.sname = sname;
					this.speed = speed;
					this.fly = function(){
						console.log(this.sname+"速度"+this.speed); 
					}
				}
				
				function Plane(fname,speed,capacity){
					Flyer.call(this,fname,speed);
				
					// Flyer.apply(this,[fname,speed]);
					
					this.capacity = capacity;
				
				}


				var  A380 = new Plane("A380",1800,555);
				A380.fly();
	****原型对象：每个函数对象都有一个原型对象；prototype
		构造函数的原型对象负责保存所有子对象共享的成员；
		建议：所有子对象共享的方法，都应定义在构造函数的原型对象中；避免重复定义方法对象浪费内存；
		说明：所有内置类型的API都在原型对象中；
		
		***解决浏览器的问题
			var str="    Hello word     ";
			if(!String.prototype.trim){
				String.prototype.trim = function(){
					return this.replace(/^\s+|\s+$/g,"");
				}
			}
			str = str.trim();
			document.write(str.replace(" ","_"));
	****扩展对象属性;2中扩展
			1.扩展共有属性：通过构造函数.prototype 添加属性
			2.扩展自有属性：通过某一个具体子对象添加属性
		判断自有属性或共有属性：
			判断自有属性：obj.hasOwnProperty("propname")
			判断共有属性：    ( "属性名" in obj)&&!obj.hasOwnProperty("propname") 
			删除属性; delete obj.属性名；仅能删除当前对象自己的属性无法删除共有属性；
		****全局变量： var n=1|window.n=1|window["n"]=1 可以被delete;;
		*****子对象不能修改原型对象:
	*****原型链：由各级对象的_proto_逐级继承形成的关系
		***获取任意对象的父级原型对象
			Obiect.getPrototypeOf(子对象)
				==>子对象._proto_
	***********typeOf()分不清数组和对象用isArray;
	***/*检测是不是Array*/
		if(!Array.isArray){
			Array.isArray=function(obj){
				//1如果Array.prototype在obj的原型链中；
				return Array.prototype.isPrototypeOf(obj);
				//2 obj instanceof 构造函数名
				//判断obj对象是否被构造函数创建
				 return obj instanceof Array;
				 //3 子对象的constructor
				  return obj.constructor==Array;
				  //4 利用object原型的toString
				  return Object.prototype.toString.call(obj)=="[object Array]" 
			}
		}
	继承：
	*********call apply(thisobj[, args])	
		call:在调用方法的一瞬间更换对象


*****内置对象**************************************************************
	内置对象：es标准中已经定义好了的，由浏览器厂商已经实现的对象
	******11个 *String Number Boolean**Array Math RegExp**Error**Function**Object**Global;
	包装类型：专门封装了原始数据类型；提供了原始类型的操作方法；

				

************************************************************************	
	***引用类型：值不保存在本地的数据类型



