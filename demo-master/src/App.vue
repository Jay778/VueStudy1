<template>
	<div id="app">
		<div class="header">
			<div class="logo1">
			<router-link to="/">
				<img src="./assets/logo.png" class="logo"/>
			</router-link>
			</div>
			<div class="right">
			<router-link to="/task" class="nav-item">任务中心</router-link>
			<router-link to="/lib" class="nav-item"> 库管理</router-link>
			<router-link to="/#" class="nav-item">教学包</router-link>
			<router-link to="/lib" class="nav-item">我的题库</router-link>
			<router-link to="/lib" class="nav-item">手机投屏</router-link>
			<router-link to="/ucenter" class="nav-item">何杰</router-link>
			</div>
		</div>
		<div class="container"><router-view></router-view></div>
	</div>
</template>

<script>
export default {
	name: 'App'
};
</script>

<style>
#app {
	background-color: rgb(244, 244, 244);
}
.header {
	
	width: 100%;
	height: 40px;
	background-color: #fff;
	font-size: 20px;
	padding-left: 120px;
	align-items: center;
	justify-content: center;
}
.logo1{
	float: left;
}
.right{
	margin-right: 150px;
	float: right;
}
.nav-item {
	width: 100px;
	margin-right: 20px;
}
.logo{
	widows: 100px;
	height: 35px;
	margin-right: 200px;
}
.container {
	width: 85%;
	margin: 0 auto;
	padding-bottom: 40px;
}
a {
	text-decoration: none;
	color: #aaa;
}
a:hover {
	color: rgb(2,165,218);
}
</style>
