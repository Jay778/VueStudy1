<template>
	<div class="container">
		<div class="side-bar">
			<router-link to="/lib1">我的班课</router-link>
			<router-link to="/lib2" >加入的班课</router-link>
			<router-link to="/lib3">管理</router-link>
		</div>
		<div class="content"><router-view /></div>
	</div>
</template>

<script>
export default {
	name: 'Lib',
	data() {
		return {};
	}
};
</script>

<style scoped>

.content{
	flex: 1 1 80%;
	text-align: left;
	background-color: #fff;
	margin-left: 0px;
	padding-bottom: 20px;
}
</style>
