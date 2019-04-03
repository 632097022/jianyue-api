<template>
	<view class="container">
		<view class="list">
			<view class="list-item">
				<text>昵称</text>
				<input v-model="nickname" class="nickname"/>
			</view>
			<view class="list-item" @tap="showActionSheet">
				<text>修改头像</text>
				<image :src="avatar" class="avatar" @tap="showActionSheet"></image>
			</view>
			<view class="list-item">
				<text>修改密码</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
	data() {
		return {
			nickname: uni.getStorageSync('login_key').nickname,
			avatar: uni.getStorageSync('login_key').avatar,
			userId: uni.getStorageSync('login_key').userId
		};
	},
	onLoad() {
	},
	methods: {
		showActionSheet: function() {
			console.log('show');
			var _this = this;
			uni.showActionSheet({
				itemList: ['拍照', '从相册选择'],
				success: function(res) {
					console.log('选中了第' + (res.tapIndex + 1) + '个按钮');
					//选择的是拍照功能
					if (res.tapIndex == 0) {
						uni.chooseImage({
							count: 1,
							sourceType: ['camera'],
							success: function(res) {
								uni.saveImageToPhotosAlbum({
									filePath: res.tempFilePaths[0],
									success: function() {
										console.log('save success');
										uni.uploadFile({
											url: 'http://192.168.43.83:8080/api/user/avatar', 
											filePath: res.tempFilePaths[0],
											name: 'file',
											formData: {
												userId: _this.userId
											},
											success: uploadFileRes => {
												console.log(uploadFileRes.data);
												_this.avatar = uploadFileRes.data;
											}
										});
									}
								});
							}
						});
					}
					//从相册选择
					if (res.tapIndex == 1) {
						uni.chooseImage({
							count: 1, //默认9
							sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都
							sourceType: ['album'], //从相册选择
							success: function(res) {
								console.log(JSON.stringify(res.tempFilePaths));
								uni.uploadFile({
									url: 'http://********:8080/api/user/avatar', 
									filePath: res.tempFilePaths[0],
									name: 'file',
									formData: {
										userId: _this.userId
									},
									success: uploadFileRes => {
										console.log(uploadFileRes.data);
										_this.avatar = uploadFileRes.data;
									}
								});
							}
						});
					}
				},
				fail: function(res) {
					console.log(res.errMsg);
				}
			});
		}
	}
};
</script>

<style scoped>
	.list-item{
		display: flex;
		height:80px;
		align-items: center;
		justify-content: space-between;
	}
	/* .nickname{
		float: right;
	} */
</style>
