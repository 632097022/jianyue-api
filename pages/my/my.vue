<template>
	<view class="logo" @click="goLogin" :hover-class="!login ? 'logo-hover' : ''">
		<image class="logo-img" :src="login ? uerInfo.avatarUrl :avatarUrl"></image>
		<view class="logo-title">
	<view class="container">
		<!-- 顶部头像和昵称区域，纵向排列 -->
		<view class="top">
			<view class="avatar-box">
				<image
					src="../../static/default.png"
					mode="scaleToFill"
					class="avatar"
					v-if="!storageData.login">
					</image>
				<image
					:src="storageData.avatar"
					mode="scaleToFill"
					class="avatar"
					v-if="storageData.login"
			></image>
				<view class="ava">
									<view class="info-box">
						<navigator url="../signin/signin"> <button type="primary" -if>点击登录</button></navigator>
						
						<navigator url="../register/register"> <button type="primary" -if>点击注册</button></navigator>
					<text v-if="storageData.login">{{ storageData.nickname }}</text>
					<view class="text-box" v-if="storageData.login">
					
						<p type="primary" @tap="signOut">个人设置</p>
					</navigator>
					</view>
		</view>
		
		
	</view>
</template>

<script>
var loginRes, _self;
export default {
	data() {
		return {
			storageData: {},
			articleCount:10,
			followCount:5,
			messageCount:66,
			integral:100,
			articles:[
				{
					id:1,
					title:'天上突然掉馅饼，真的就砸中了我！',
				},
				{
					id:2,
					title:'你是被关注了还是被套路了？',
				},
				{
					id:3,
					title:'学会用数据讲故事，职场必备技能！',
				},
				{
					id:4,
					title:'这又是一篇没有“稿费”的文章',
				}
			]
		};
	},
	onLoad: function() {},
	onShow: function() {
		const loginKey = uni.getStorageSync('login_key');
		console.log("my-vue page show");
		if (loginKey) {
			console.log(loginKey);
			this.storageData = {
				login: loginKey.login,
				nickname: loginKey.nickname,
				avatar: loginKey.avatar
			};
		}else{
			this.storageData ={
				login: false
			}
		}
	},
	methods: {
		
	}
};
</script>

<style scoped>
	page {
		background-color: #f8f8f8;
	}
.top {
	display: flex;
	flex-direction: column;
	text-align: center;
	height: 100px;
	margin-top: 5px;
}
.avatar-box{
	flex: 1 1 30%;
}
.info-box{
	flex: 1 1 70%;
	display: flex;
	align-items: center;
	justify-content: center;
}
.setting-txt{
	color: #4cd964;
	margin-left: 15px;
}
.center{
	display: flex;
	justify-content: center;
}
.info{
	flex: 1 1 25%;
	display: flex;
	flex-direction: column;
	text-align: center;
	
	border-right: 1px solid #4cd964;
}
.title{
	font-size: 14pt;
}
.content{
	margin-top: 20px;
}
</style>