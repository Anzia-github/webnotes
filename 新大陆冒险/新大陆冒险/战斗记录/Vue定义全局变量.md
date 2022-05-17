- 放到[[Vue]]的[[prototype]]属性中
- 在全局的[[JS]]中自定义全局变量然后引入
	- `import global_msg from '../js/global.js'`
- 在main.js中将global.js挂载到[[Vue]].[[property]]中
	- main.js
	```JS
	import import global_msg from '../js/global.js
	Vue.property.$global_msg = global_msg
	```
	- 页面中使用
	```html
	<template>
    <div>
        <button @click="clickMe">点我</button>
    </div>
	</template>
	<script>    
	    export default {
	        data(){
	            return{}
	        },
	        methods:{
	            clickMe(){
	                alert(this.$global_msg.host);    //localhost:8080
	            }
	        }
	    }
	</script>
	```