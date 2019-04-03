<!-- <template>
	<view class="container">
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
						<navigator url="../signin/signin" v-if="!storageData.login">点击登录</navigator>
						<text v-if="storageData.login">{{ storageData.nickname }}</text>
					<view class="text-box" v-if="storageData.login">
					<navigator url="../setting/setting">
						<p type="primary" @tap="signOut">个人设置</p>
					</navigator>
					</view>
				</view>
			</view>
		</view>
		</view>
		
		<view class="content" v-if="storageData.login">
			<view class="card">
				<text>{{articleNum}}</text>
				<br/>
				<text>文章</text>
			</view>
			<view class="card">
				<text>{{attentionNum}}</text>
				<br/>
				<text>关注</text>
			</view>
			<view class="card">
				<text>{{messageNum}}</text>
				<br/>
				<text>消息</text>
			</view>
			<view class="card">
				<text>{{creditNum}}</text>
				<br/>
				<text>积分</text>
			</view>
		</view>
		<view class="text" v-if="storageData.login">
			<view class="list">
				<view class="article" v-for="(article,index) in articles " :key="index">
					<text>{{article.title}}</text>
				</view>
			</view>
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
			articleNum:'10',
			attentionNum:'5',
			messageNum:'66',
			creditNum:'100',
		articles:[
			{
				id:'1',
				title:'天上突然掉馅饼，真的就砸中了我！',
			},
			{
				id:'2',
				title:'你是被关注了还是被套路了？',
			},
			{
				id:'3',
				title:'学会用数据讲故事，职场必备技能！',
			},
			{
				id:'4',
				title:'这又是一篇没有“稿费”的文章'
			}
		],
		};
	},
	onLoad: function() {},
	onShow: function() {
		const loginKey = uni.getStorageSync('login_key');
		console.log("come");
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
.top {
	display: flex;
	flex-direction: column;
	height: 70px;
	margin-top: 10upx;
}
.avatar-box{
	flex: 1 1 30%;
	text-align: center;
}
.info-box{
	flex: 1 1 90%;
	display: flex;
	align-items: ;
	/* justify-content: flex-start;
	justify-content: space-between; */
	margin-left: 250upx;
}
.ava{
	display: flex;
}
.text-box{
	/* margin-left: 400upx;
	margin-top: -40upx; */
	margin: 0 auto;
	color: green;
}
.content{
	display:flex;
	flex-direction:row;
	text-align: center;
}
.card{
	padding-left: 100upx;
	margin-top: 100upx;
	margin-left: -10upx;
	border-right: 1px solid #EEEEEE;
}
.article{
	margin-top: 50upx;
	font-size: 40upx;
	border-bottom: 1px solid #EEEEEE;
	height: 100upx;
}
.list{
	padding-top: 30upx;
}
</style> -->
<template>
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
			</view>
			<view class="info-box">
				<navigator url="../signin/signin" v-if="!storageData.login">点击登录</navigator>
				<text v-if="storageData.login">{{ storageData.nickname }}</text>
				<navigator url="../setting/setting" v-if="storageData.login">
					<text class="setting-txt">个人设置</text>
				</navigator>
			</view>
		</view>
		
		<!-- 中间文章数量、好友数量、消息数量等统计区域，横向排列 -->
		<view class="center" v-if="storageData.login">
			<view class="info">
				<text class="title">{{articleCount}}</text>
				<text>文章</text>
			</view>
			<view class="info">
				<text class="title">{{followCount}}</text>
				<text>关注</text>
			</view>
			<view class="info">
				<text class="title">{{messageCount}}</text>
				<text>消息</text>
			</view>
			<view class="info">
				<text class="title">{{integral}}</text>
				<text>积分</text>
			</view>
		</view>
		
		<view class="content" v-if="storageData.login">
			<view class="list">
				<view class="list-item" v-for="(article, index) in articles" :key="index">
					<text>{{article.title}}</text>
				</view>
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
	color: #00B26A;
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
	
	border-right: 1px solid #eee;
}
.title{
	font-size: 14pt;
}
.content{
	margin-top: 20px;
}
</style>