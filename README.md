# ali-yuebin
阿里巴巴抢月饼事件，代码模拟重现

<h3>根据知乎上的描述，当事程序员代码可能是这样的</h3>

PS：已优化，这样只会在最快的时间内点一次
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>抢月饼</title>
</head>
<body>
	<button id="button">抢购按钮</button>	
	<p><input type="text" id="val">验证码：QS5N</p>
	<p id="content"></p>
	<script>	
		let button=getById("button");
		let content=getById("content");
		let val=getById("val");
		//模拟开抢时间
		let timer1=setInterval(()=>{
			let date=new Date();
			let datestr=date.toString().substr(15,9);
			content.innerHTML=datestr;
			if(date.getHours().toString()==12&&date.getMinutes().toString()==05&&date.getSeconds().toString()==00){
				button.innerHTML="开始秒杀";
			}
		},50)
		//抢月饼脚本部分
		let flag=0;
		let timer2=setInterval(()=>{

			if(button.innerHTML=="开始秒杀"){
				val.value="QS5N"
				button.click();
				console.log('点击成功');
				flag=1;
			}
			if(flag==1){
				clearInterval(timer2);
			}			
		},50)
		function getById(obj){
			return document.getElementById(obj);
		}
	</script>
</body>
</html>
```
