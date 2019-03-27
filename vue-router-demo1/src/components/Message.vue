<template>
<!-- 根容器 -->
	<div class="container">
		<h2>消息</h2>
		{{msg}}
	</div>
</template>

<script>
	export default{
		name:'Index',
		data(){
			return{
				msg:'这是消息页面'
			};
		}
	}
</script>
<!-- scoped:只对本页面有用 -->
<style scoped>
</style>

