<template>
	<!-- 根容器 -->
	<div class="container">
		<router-link to="/new_course"><button class="btn">新建班课</button></router-link>
		<div class="top">
			<p>进行的班课</p>
			<p>{{courses.length}}个进行的班课</p>
		</div>
		<hr />
		
		
		<div class="course-conainer">
			<div class="course" v-for="(course, index) in courses" :key="index">
				<div class="course-cover">
					<router-link :to="'/course/'+course.courseId">
						<img :src="course.cover"/>
					</router-link>
				</div>
				<div class="course-class">
					<p class="title">{{course.courseClass}}</p>
				</div>
				<div class="course-name">
					<p class="title">{{course.courseName}}</p>
				</div>
				<div class="course-code" v-if="loginUserId === course.userId">
					{{course.courseCode}}
				</div>
			</div>
		</div>
	<div class="end">
		<p>已结束的班课</p>
		<p>{{ends.length}}个结束的班课</p>
	</div>
	<hr>
	<div class="course-conainer">
			<div class="course" v-for="(course,index) in ends" :key="index">
			<div class="course-cover">	
			    <img :src="course.cover"/>
			</div>
			<div class="course-class">
				<p class="title">{{course.courseClass}}</p>
			</div>
			<div class="course-name">
				<p class="title">{{course.courseName}}</p>
			</div>
			<div class="course-code" v-if="loginUserId === course.userId">
				{{course.courseCode}}
				<button @click="deleteCourse(course.courseId,index)" class="btn">删除</button>
			</div>
		</div>
	</div>
</div>
</template>
<script>
export default {
	name: 'Index',
	data() {
		return {
			loginUserId: 1,
			courses: [],
			ends: []
		};
	},
	methods: {
		deleteCourse: function(courseId,index) {
			var _this = this;
			this.$http({
				method: 'delete',
				url: 'http://localhost:8080/api/course/'+courseId
			}).then(function() {
				alert('班课删除成功');
				 _this.ends.splice(index,1);
			});
		}
	},
	created() {
		var _this = this;
		this.$http.get('http://localhost:8080/api/courses').then(function(response) {
			_this.courses = response.data;
		});
		this.$http.get('http://localhost:8080/api/ends').then(function(response) {
			_this.ends = response.data;
		});
	}
};
</script>
<style scoped>
	div{
		font-family: Roboto, "Lucida Grande", "Lucida Sans Unicode", Helvetica, Arial, Verdana, "微软雅黑", sans-serif;
	}
	.top{
		width: 80%;
		margin: 0 auto;
		display: flex;
		justify-content: space-between;
	}
.end{
		width: 80%;
		margin: 0 auto;
		display: flex;
		justify-content: space-between;
	}
.container {
	padding-top: 20px;
}
.course-conainer {
	display: flex;
	flex-wrap: wrap;
}
.course {
	margin: 40px;
	margin-top:20px ;
	width:240px;
	height:350px;
	margin-right:20px;
	margin-bottom:50px;
	background-color:#fff;
	display:flex;
	flex-direction:column;
	padding-bottom:30px;
}
.course-cover img {
	width: 100%;
	height: 280px;
}
.title {
	font-size: 16px;
	color: #333;
}
.btn {
	 border: 1px #3083ff solid;
	border-radius: 4px;
	background-color: #3487ff;
	box-shadow: 0 5px 8px 0 rgba(24,95,255,.1);
	color: #fff;
	text-align: center;
	font-weight: lighter;
	background-image: linear-gradient(0deg,#398bff,#3083ff);
	width: 100px;
	height: 40px;
	margin: 40px 0 8px;
	font-size: 17px;
}
.course-code {
	color: rgb(0, 187, 221);
}
</style>
