<template>
	<div>
		<h1>hello hello {{timer}}</h1>
		<h2>一共点击了 {{count}} 次按钮， <span v-if="myFlag">you watch me now!</span></h2>
		<ul>
			<li>一去二三里</li>
			<li>烟村四五家</li>
			<li>亭台六七座</li>
			<li>八九十枝花</li>
		</ul>
		<button class="btn" v-on:click="changeColor">点击修改字体颜色</button>
		<h1 class="title">{{title}}</h1>
	</div>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）

export default {
	name: 'Test',
	props: {
		title: String,
	},
	components: {
	},
	// 定义属性
	data() {
		return {
			timer: new Date().toString(),
			count: 0,
			myFlag: false,
			log: null,
		}
	},
	// 计算属性，会监听依赖属性值随之变化
	computed: {
		
	},
	// 监控data中的数据变化
	watch: {},
	// 方法集合
	methods: {
		changeColor(){
			this.count++;
			this.myFlag = !this.myFlag;
			if(this.myFlag){
				document.getElementsByTagName('ul')[0].style.color = 'red';
			}else{
				document.getElementsByTagName('ul')[0].style.color = 'green';
			}
		}
	},
	// 生命周期 - 创建完成（可以访问当前this实例）
	created() {
		console.log(this);
	},
	// 生命周期 - 挂载完成（可以访问DOM元素）
	mounted() {
		this.log = setInterval(() => {
			this.timer = new Date().toString()
		}, 1000)
	},
	// 生命周期 - 创建之前
	beforeCreate() {
		console.log('未创建');
	}, 
	// 生命周期 - 挂载之前
	beforeMount() {
		console.log('未挂载');
	},
	// 生命周期 - 更新之前
	beforeUpdate() {
		// console.log('待更新');
	},
	// 生命周期 - 更新之后
	updated() {
		// console.log('已更新');
	},
	// 生命周期 - 销毁之前
	beforeUnmount() {
		clearInterval(this.log);
		this.log = null;
		console.log('清除成功');
	},
	unmounted() {}, // 生命周期 - 销毁完成
	activated() {}, // 如果页面有keep-alive缓存功能，这个函数会触发
}
</script>

<style scoped>
	li {
		list-style : none;
		margin: 5px 0;
	}
	.title{
		position: relative;
		margin-top: 200px;
	}
</style>