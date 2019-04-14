<template>
	<view class="content">
		
		<view class="top1">
			<view class="cover1">
				<text>话题»</text>
			</view>
			<view>
			<img src="static/sc1.png"> 
			<img src="static/sc.png">
			</view>
		</view>
			<view class="card" v-for="(course,index) in class1" :key="index">
				<view class="cover">
					<img :src="course.avatar">
				</view>
				<view class="course-clas">
					<text>{{course.name}}</text>
					<p class="name">{{course.Cname}}</p>
				</view>
				<view class="course-code">
					<text>{{course.Tname}}</text>
				</view>
			</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				class1: [{
						name: '赛事资讯',
						Cname: '韦德迎着塔图姆投进三分，完成本节最后一攻',
						avatar: 'static/nba.png'
						
					},
					{
							name: '实政新闻',
							Cname: '习主席这些话，致敬民族最闪亮的坐标',
							avatar: 'static/u.png'
							
						},
						{
								name: '历史旧闻',
								Cname: '国民党整编74师之谜',
								avatar: 'static/book.png'
								
							},
							{
									name: '军事频道',
									Cname: '命悬一线的俄罗斯航母舰载机',
									avatar: 'static/air.png'
									
								},
								{
										name: '国际新闻',
										Cname: '阿富汗是如何从天堂坠入地狱',
										avatar: 'static/new.png'
										
									},
									{
											name: '天气预报',
											Cname: '华北各省市气温回升',
											avatar: 'static/t.png'
											
										},
														
					
				]
			}
			
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		width: 100%;
		margin: 0 auto;
		flex-wrap: wrap;
		padding-top: 10upx;
		flex-direction: column;
	}
	.top1 {
		width: 100%;
		height: 100upx;
		display: flex;
		justify-content: space-between;
		background-color:white;
	}
	.cover{
		display: flex;
	}
	.cover1{
		margin-top: 20upx;
	}
	img{
		width: 70upx;
		height: 70upx;
	}
	.card {
		border-top: 1upx solid #DDDDDD;
		border-bottom: 1upx solid #DDDDDD;
		width: 100%;
		height: 150upx;
		display: flex;
		/* 垂直方向居中 */
		align-items: center;
	}
	.cover img {
		width: 70upx;
		height: 70upx;
	}
	.course-clas{
		margin-left: 20upx;
		flex: 1 1 10%;
	}
	.name{
		font-size: small;
		color: #8F8F94;
	}
	.course-code {
		
		color: #8F8F94;
		margin-top: -40upx;
	}
</style>
