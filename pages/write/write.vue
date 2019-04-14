<template>
	<view>
	<view class="container">写文章</view>
    <textarea placeholder="输入内容" v-model="content" class="content" />
	<view class="read">
       <text >预览</text>
		
	</view>
    <button class="green-btn" @tap="postArticle">发布文章</button>
</view>
</template>

<script>
</script>

<style scoped="scoped">
	.read{
		margin-bottom: 50px;
	}
</style>
