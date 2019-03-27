<template>
	<div class="container">
		<h2>任务中心</h2>
		<div class="preview">
			<img :src="imgUrl" />
			</div>
			<form>
				<div class="upload">
					选择文件
					<input type="file" @change="getFile($event)" />
				</div>
				<br />
				<button @click="submit($event)" class="sub-btn">提交</button>
			</form>
	</div>
</template>

<script>
export default {
	name: 'Task',
	data() {
		return {
			imgUrl:'https://static-cdn-oss.mosoteach.cn/mssvc/icons/icon_cc_cover1@2x.png',
			file:''
			
		};
	},
	methods: {
		handleClick: function(){
			document.getElementById('coverFile').click();
		},//图片预览
		getFile:function(event){
			this.file=event.target.files[0];
			var windowURL=window.URL || window.webkitURL;
			alert(windowURL.createObjectURL(this.file));
			this.imgUrl=windowURL.createObjectURL(this.file);
		},
		submit:function(event){
			event.preventDefault();
			let formData=new FormData();
			formData.append('file',this.file);
			this.$http.post('http://localhost:8080/upload',formData)
			.then(function(response){
				alert(response.data);
				this.imgUrl=response.data;
			});
		}
	}
};

</script>
<style scoped>
	.preview{
		width: 150px;
		height: 150px;
		border: 2px dashed #aaa;
		cursor: pointer;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.icon-plus{
		width: 70px;
		height: 70px;
	}
	.preview img{
		width: 100%;
		height: 100%;
	}
	.sub-btn{
		width: 120px;
		height: 35px;
		border-radius: 10px;
		outline: none;
		background-color: #333333;
		color: #ffffff;
	}
	.upload{
		margin-top: 10px;
		display: inline-block;
		width: 120px;
		height: 35px;
		border: 1px solid #99d3f5;
		border-radius: 4px;
		background-color: #d0eeff;
		color: #000;
		text-align: center;
		cursor: pointer;
	}
	.upload input{
		width: 100%;
		height: 100%;
		opacity: 0;
	}
	.upload:hover{
		background: #aadffd;
		border-color: #78c3f3;
		color: #004974;
		text-decoration: none;
	}
</style>
