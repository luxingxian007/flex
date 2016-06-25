# flex
使用Flex布局及原生态JS制作简单功能计算器
# 案例展示 [演示效果Demo](http://luxingxian007.github.io/flex/index.html/)
# 案例用法
## step1 html格式
~~~
<div class="cale">
		<div class="showbox">
			<input type="text" id="show"/>
		</div>
		<div class="buttons">
			<input type="button" value="c" id="clear"/>
			<input type="button" value="←" id="del"/>
			<input type="button" value="/"/>
			<input type="button" value="*"/>
			<input type="button" value="7"/>
			<input type="button" value="8"/>
			<input type="button" value="9"/>
			<input type="button" value="-"/>
			<input type="button" value="4"/>
			<input type="button" value="5"/>
			<input type="button" value="6"/>
			<input type="button" value="+"/>
			<input type="button" value="1"/>
			<input type="button" value="2"/>
			<input type="button" value="3"/>
			<input type="button" value="0" class="zero"/>
			<input type="button" value="." class="point"/>
			<input type="button" value="=" id="eq"/>	
		</div>
	</div>
~~~
## step2 css格式
~~~
    *{margin: 0;padding: 0;box-sizing: border-box;}
		.showbox{display: flex;width: 100vw;height: 30vh;}
		.showbox input{flex:1;background-color: rgb(227,231,234);font-size: 7vw;padding: 7vw;border: none;}
		.buttons{display: flex;width: 100vw;height: 70vh;flex-wrap: wrap;}
		.buttons input{flex:0 0 25vw;height: 25vw;font-size: 7vw;}
		.buttons .zero{flex:0 0 50vw;}
		#eq{height: 50vw;margin-top: -25vw;background-color: rgb(250,116,45);}
		#eq:active{background-color: rgba(250,116,45,.6);}
~~~
## step3 js内容
~~~
window.addEventListener("load",init,true);
		function init(){
			var show=document.getElementById("show");
			var eq=document.getElementById("eq");
			var del=document.getElementById("del");
			var clear=document.getElementById("clear");
			var inputs=document.getElementsByTagName("input");
			
			for(var i=0;i<inputs.length;i++){
				if(inputs[i]==eq||inputs[i]==clear||inputs[i]==del){continue;}
				inputs[i].addEventListener("click",changeit,true);
				function changeit(){
					show.value+=this.value;
				}
			}
			eq.onclick=function(){
				show.value=eval(show.value);
			}
			clear.onclick=function(){
				show.value="";
			}
			del.onclick=function(){
				var len=show.value.length;
				show.value=show.value.substring(0,len-1);
			}
		}
~~~
