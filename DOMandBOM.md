<script>
**********DHTML:动态网页技术的统称；
	DHTML = HTML + CSS + JS;
	HTML XHTML DHTML XML 
	HTML：超文本标记语言
	XHTML：严格的html语言标准；
	DHTML:动态网页技术的统称；
	XML：可扩展的标记语言 语法同HTML（可以自定义标签）专门又来存储或传输的结构化数据；逐渐被json替代了；
	*****BOM vs DOM
		BOM 浏览器对象模型（API）专门操作浏览器窗口的API
			没标准：注意兼容问题
		DOM 文档对象模型的api 专门操作网页内容的API;
			可以对网页中任意对象，做任何修改；
			DOM是标准 90%以上浏览器严格兼容
		核心DOM 操作所有结构化文档(XML HTML)的通用API
		HTML DOM :针对html文档的简化API;hTML dom不能完成所有的功能，结合核心DOM
		HTML DOM :网页中一切都是对象；
				  同一网页中的所有对象在内存中父子相连形成DOM
		DOM 增删查改
***DOM*********************************************
	**文档中的元素，属性，文本，注释等都被看做一个节点对象（Node所有节点对象的父类型）;
	******当网页被加载进内存时,浏览器会为网页创建一个document对象。所有的节点对象都是document对象的子节点；
	document,封装了对网页中所有字节点的增加 删除，查找
	****Node 定义了三个公共属性 nodeType nodeName nodeValue
		nodeType:节点类型的数值；
			专门用于判断获得的节点类型；
			元素节点，返回1；
			文本节点，返回3；
		nodeName:节点名称
			元素节点，返回标签名；
			文本节点，返回#text；
			***强调：nodeName返回的全是大写的标签名；
		nodeValue:节点值
			元素节点：null;
			文本节点：返回文本的内容；
	****节点关系：  
		**父子：parentNode (childNodes firstChild lastChild)会拿到空节点
		**兄弟： previousSibling  nextSibling
			childNodes:类数组对象，*****动态集合*****
				for(var r=0,i=0,len=tbody.childNodes.length; i<len; i++);
	***** 遍历：从指定父元素开始，按照深度优先的原则遍历所有各级子节点；
			1.定义一个函数，查找任意父节点下的子节点；
			2.以深度优先为原则，递归调用函数本身；
		递归：
			何时使用递归：1.遍历不确定层级深度的树形结构
								比如网页中的元素 网盘的文件夹结构
						 2.不确定深度的多层级管理结构；


			var blanks = [];
			function getChildren(parents){
				console.log(
					blanks.join("")+"|-"+(parent.nodeType!=3?
						parent.nodeName:parent.nodeValue)
					)
				if(parent.childNodes.length>0){
					blanks.push("\t");
				}
				for(var i=0,len=parent.childNodes.length; i<len; i++){
					getChildren(parent.childNodes[i]);
				}
				blanks.pop();
			}
			
			getChildren(document);
	********元素树*****
		元素树：有元素节点组成的树的结构
			其实有一组和节点树6个属性对应的元素树属性；
					  节点树			元素树
			父对象	   parentNode     parentElementNode
			所有子对象  childNodes     children
			第一个子对象 firstChild    firstElementChildren
			最后子对象	lastChild     lastElementChild
			前一个兄弟   previousSibling   previousElementSibling
			后一个兄弟	nextSibling     nextElementSibling
		**何时使用：只要仅希望遍历元素节点时，就用元素树
		**但是IE8不兼容，children可用
		********var blanks = [];
				function getChildren(parent){
					console.log(
						blanks.join("")+"|-"+(parent.nodeType!=3?
							parent.nodeName:parent.nodeValue)
						)
					 
					if(parent.children.length>0){
						blanks.push("\t");
					}
					for(var i=0,len=parent.children.length; i<len; i++){
						getChildren(parent.children[i]);
					}
					blanks.pop();
				}
				
				getChildren(document);
		*   遍历API 2个 兼容性不好
			1.深度优先遍历：NodeIterator:节点迭代器；

			2.自有遍历：TreeWlaker;
	*查找：API  HTML CSS  其他
		 1.id: var ele = document.getElementById("id");
		 2.按标签名查找：(向下爬树的手段) 
		 		var elems = parent.getElementsByTagName("标签名");
		 		***elems***动态集合
		 3.name:(专门查找表单元素);
		 		var elems=  document.getElementsByName("name属性")；
		 		***elems***动态集合
		 4.className;
		 	var elems = pareent.getElementsByClassName("className");
		 5.Selector; jquery的核心
		 	var elem = parent.querySelector(selectors[, NSResolver])
		 	var elems = parent.querySelectorAll("任意选择器")；
	***HTMLelement；
		HTML文档中每种HTML元素都对应一个专门的类型
			example:<bttton> HTMLButtonElement
		核心DOM：增删查改
		HTMLdom:修改属性；
		1.获取或修改元素内容：3个属性
			1.innerHTML:获得元素开始标签和结束标签之间的html内容(包含标签)
				获得html原文内容时
					1.删除父元素下所有子元素：parent.innerhtml ="";	
					2.批量替换所有父元素下的所有子元素：parent.innerHTML="所有子元素标签组成的html";		
				批量修改设置子元素的内容；
			2.textContent(Dom标准)/innerText(ie8)：获得开始标签和结束标签之间的纯文本内容--子HTML
			3.获得文本节点的内容：nodevalue;
		2.元素内容：
		3.元素属性：所有的元素都有attributes属性返回节点的属性集合，即NameNodeMap--一类数组对象；
			****获得属性的方法：四种
				1.element.attributes[下标].value;
				2.var value = element.attribute['属性名'];
				3.element.getAttribute('属性名').value
				****4. var value = element.getAttribute("属性名")；
					只要获得任意属性的值
			****修改属性：2种
				****1.element.setAttribute(name, value[, iecaseflag]) IE8不支持 element.setAttributes['属性名']=value;
				2.element.setAttributeNode(newAttr);
			****移除属性
				****element.removeAttribute("name");
				element.removeAttributeNode("oldAttr")
			**判断属性是否存在：
				element.hasAttribute("属性名")；
				element.hasAttributes()判断是否拥有属性；
			**property vs Attribute
				property:对象在内存中存储的属性 用.访问
				Attribute:元素对象在开始标签中定义的HTML属性和自定义属性
				如果访问HTML标准属性时二者完全一致；
					example；<a href="http://" >
							a.href /  a.getAttribute("href");
				如果访问自定义属性时 二者不通用
				<li data-age="29"><li>
				读取自定义属性：li.data-age? X  
									li.getAttribute("data-age");
				设置自定义属性：  li.setAttribute("data-age",29);
				****类数组对象转化为标准数组对象
					lis = Array.prototype.slice.call(lis);	
	**创建删除节点
		*创建节点：
			创建元素节点：
			1.创建空元素对象： var newElem=document.creatElement("标签名");
			2.设置必要属性：
				newElem.属性名="值"；
				newElem.innerHTML = "文本"；
			3.将元素对象挂载到父元素下；
				1.追加;parent.appendChild("newChild");	
					只有在页面中已有的元素添加在元素才会渲染；
		*创建文档对象：documentfragment
			文档片段：内存中，临时存储多个子节点的存储空间
			现将所有的评级元素先追加到文档片段中
			将文档片段一次性追加到父元素下；
			文档片段不追加；
			var frag = document.createDocumentFragment();
			frag.appendChild("newChild")
			table.appendChild(frag);

		***eval();
		***insertBefore(newChild, refChild)
			在父元素中的指定子节点之前添加一个新的子节点(也可用于移动子节点)；
		***删除节点： parent.removeChild("oldChild");
			删除自己：oldElem.parentNode.removeChild("oldChild")
		***替换节点;parent.replaceChild(newChild, oldChild)
		***
		****Select对象
			属性：
				option:获得当前select下的所有option
				option[i]:获得当前select下i位置的option
				selection：获得当前选中的option的下标
			方法：
				add(new option)
					同append;
				remove(index);
		****option对象：指代option下的某一个option元素
			如何创建：var newOpt = new Option(innerHTML,value);
			相当于：var newOpt = document.creatElement("option");
			newOpt.innerHTML = "内容"；
			newOpt.value="值"；
			创建设置同时追加;
			selcet.add(new Optin(innerHTML,value));
			属性：index:获取当前option的下标位置，专用于删除；
				  selected:可当做bool用
				  	如果当前option被选中，返回true否则返回false;
		****form对象：
			如何找到forms对象
				var document.forms[i];
			如何找到form中的数据采集元素
				form.elements[i/name];
			事件：onsubmit	
		让元素获得或者失去焦点
			elem.focus();
			elem.blur();
		获得当前正在获得焦点的元素;document.activeElement
		表单事件：
			onsubmit:在表单正式提交前自动触发
				对整个表单执行验证
					elem.onsubmit = function(){
						只要任意一个验证未通过，
						就取消事件；
							1.获得event对象e
							var e = window.event||arguments[0];
							if(e.preventDefault())//DOM
							{
								e.returnValue = false;
							}
							2.表单提交：
								直接点击sunbmit按钮
								如果当前form中的任意元素获得焦点，可按回车自动提交
								只要自动表单提交前；都会首先出发onsubmit，可做验证

					}



**BOM**********************
	bom:window navigator event screen 
	window 对象:2个角色
		1.充当全局对象！
		2.包含BOM常用对象
		****属性
			1.窗口大小与位置
				innerHeight/Width:文档显示区的大小
				outerHeight/Width:窗口大小
				pageXOffset/pageYOffset 文档左上角到文档
			2.screen.height/width:桌面完整分辨率的宽高
			  screen.availHeight/availWidth:去掉任务栏后剩余分辨率的宽高
			3.调整大小：window.resizeTo(width, height);
								resizeBy(dw, dh);
			位置：
			获得窗口位置坐标：
				window.screenLeft||window.screenX
				window.screenTop||window.screenY
			将窗口移动到指定坐标：window.moveTo(x, y);
			事件发生时鼠标的坐标：
				相对于整个屏幕的坐标event.screenX|screenY；



			打开新链接：
				1.在当前窗口打开连接，可后退
				2.在当前窗口打开连接，禁止后退
					只能js:location.replace("新url")；		
				3.在新窗口打开连接，可重复打开

				4.在新窗口打开新连接，只能打开一个
		**history:window对象中保存当前窗体访问过的url历史记录栈
			history.go(1);前进一次
				go(-1);倒退一次
				go(0);重新刷新
				go(n)前进或者后退n次
		***location:当前窗口正在打开的url地址对象
			location.search:获得url中的查询字符串
				如果进一步获得参数名和参数值：先按&分割再按=分割；
			location.replace("新的url"):在当前窗口打开新连接不可后退
			location.asin()
			location.reload([forceGet])
		***screen；封装了当前屏幕的显示信息
			screen.height/width:完整屏幕宽高
			availWidth/height去掉任务栏后剩余宽高
 *******事件：对象状态的改变（浏览器触发或人为触发的）
 		用户点击/鼠标经过/按下键盘/窗口滚动/
 		事件处理函数：当事件触发时自动执行的函数；
 		 鼠标事件：键盘事件 ：状态事件
 		**事件处理：
 			事件定义（绑定事件处理函数）：3种
 				html:<标签 on事件名="函数调用/js语句">
 				js:element.on事件名=函数对象；
 					element.addEventListener("事件名(click)", 函数对象, 是否在捕获阶段触发)绑定事件监听；
 					IE8:element.attachEvent("on事件名", "函数对象")
 			*******时间周期：从浏览器捕获到事件后，一直到最后一个事件触发完，经历的过程；
 				DOM标准的：3个阶段
 					1.捕获：由外向内捕获：从最外层html元素开始，向内层记录元素绑定的时间的处理函数到目标元素为止
 					2.目标触发：自动执行目标元素上绑定的事件处理函数；
 					3.事件冒泡：从目标元素的父元素开始，逐层向上执行的事件处理函数，到最外层html结束；
 				IE8的事件周期2个阶段；没有捕获；
 					可以用 addEventListener(event, listener, useCapture)  true/false来判断 函数在捕获阶段触发还是在冒泡阶段触发
 		*****event对象：当事件发生时自动创建；封装了事件信息
 			1.目标元素对象：var src=srcElement(ie)||target(dom)
 			2.
	****navigator

