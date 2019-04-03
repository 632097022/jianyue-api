<template>
	<view class="container">
		<view class="list">
			<view class="list-item"><text>文章推送</text></view>
			<view class="list-item"><text>新消息推送</text></view>
			<navigator url="../user_info/user_info">个人资料</navigator>
		</view>
		<button @tap="logout" class="green-btn">退出当前账号</button>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	onLoad() {
		uni.setNavigationBarTitle({
			title: '设置'
		});
	},
	methods: {
		logout: function() {
			console.log('log out');
			uni.removeStorageSync('login_key');
			uni.showToast({
				title: '已经退出当前账号'
			});
			uni.navigateBack();
		}
	}
};
</script>

<style></style>

<!-- <template>
	<view class="container">
		<view class="list">
			<text class="list-head">常规设置</text>
			<uni-list>
				<uni-list-item title="更改主页"></uni-list-item>
				<uni-list-item title="编辑个人简介"></uni-list-item>
				<uni-list-item title="查看消息" show-badge="true" badge-text="5"></uni-list-item>
				<uni-list-item
					title="开启消息通知"
					show-switch="true"
					show-arrow="false"
				></uni-list-item>
			</uni-list>
			<text class="list-head">其他设置</text>
			<uni-list>
				<uni-list-item
					title="软件更新"
					show-arrow="false"
					show-extra-icon="true"
					:extra-icon="{ color: '	#FF8247', size: '22', type: 'refresh-filled' }"
				></uni-list-item>
				<uni-list-item
					title="未绑定"
					show-arrow="false"
					show-extra-icon="true"
					:extra-icon="{ color: '	#D3D3D3', size: '22', type: 'weibo' }"
				></uni-list-item>
				<uni-list-item
					title="微信绑定"
					show-arrow="false"
					show-extra-icon="true"
					:extra-icon="{ color: '#4cd964', size: '22', type: 'weixin' }"
				></uni-list-item>
				<uni-list-item
					title="未绑定"
					show-arrow="false"
					show-extra-icon="true"
					:extra-icon="{ color: '	#D3D3D3', size: '22', type: 'qq' }"
				></uni-list-item>
			</uni-list>
			<text class="list-head1"></text>
			<uni-list>
				<uni-list-item title="绑定账号遇到问题"></uni-list-item>
				<uni-list-item title="重置密码"></uni-list-item>
			</uni-list>
			<view class="list-item">
				<button type="primary" @tap="logout">退出当前账号</button>
			</view>
		</view>
	</view>
</template>

<script>
import uniList from '@/components/uni-list/uni-list.vue';
import uniListItem from '@/components/uni-list-item/uni-list-item.vue';
/* import 导入的其它组件 */
import uniIcon from '@/components/uni-icon/uni-icon.vue';
export default {
	data() {
		return {
			/* ... */
		};
	},
	components: {
		uniList,
		uniListItem,
		uniIcon
	},
	onLoad() {
		uni.setNavigationBarTitle({
			title: '设置'
		});
	},
	methods: {
		logout: function() {
			console.log('log out');
			uni.removeStorageSync('login_key');
			uni.showToast({
				title: '已经退出当前账号'
			});
			uni.navigateBack();
		}
	}
};
</script>

<style scoped>
.list-head {
	display: flex;
	font-size: 12px;
	color: #ff6a6a;
	align-items: center;
	height: 30px;
	margin-left: 15px;
}
.list-head1 {
	height: 15px;
	background: #eeeeee;
}

uni-list-item {
	display: flex;
}
</style>
 -->
