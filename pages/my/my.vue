<template>
	<view class="container">
		<view class="user-section">
			<view class="avatar-wrapper">
				<image class="avatar" src="/static/logo.png" mode="aspectFill"></image>
			</view>
			<view class="user-info">
				<text class="name">江农学子</text>
				<text class="id">23级 数字媒体技术</text>
			</view>
		</view>

		<view class="list-section">
			<view class="item" @click="handleCollect">
				<text>我的收藏</text>
				<view class="arrow-icon"></view>
			</view>
			<view class="item" @click="handleFeedback">
				<text>反馈建议</text>
				<view class="arrow-icon"></view>
			</view>
			<view class="item" @click="handleVersion">
				<text>版本信息</text>
				<text class="version">v1.0.0</text>
			</view>
		</view>
	</view>
</template>

<script setup>

const handleCollect = () => {
	uni.showToast({
		title: '功能开发中...',
		icon: 'none',
		duration: 2000
	});
};


const handleFeedback = () => {
	uni.showModal({
		title: '反馈建议',
		content: '感谢您的关注！请将建议发送至校内邮箱：jxau_support@edu.cn',
		showCancel: false,
		confirmText: '我知道了',
		confirmColor: '#2d6a4f' 
	});
};


const handleVersion = () => {
	uni.showModal({
		title: '关于项目',
		content: '本项目由 23 级数媒同学独立开发，基于 Vue3 + uni-app 框架。',
		showCancel: false
	});
};
</script>

<style scoped>
.container { background: #f8f8f8; min-height: 100vh; }
.user-section { 
	background: #2d6a4f; padding: 60rpx 40rpx; 
	display: flex; align-items: center; 
}
.avatar-wrapper { 
	width: 120rpx; height: 120rpx; border-radius: 60rpx; 
	background: #fff; margin-right: 30rpx; overflow: hidden;
}
.avatar { width: 100%; height: 100%; }
.name { color: #fff; font-size: 36rpx; font-weight: bold; display: block; }
.id { color: rgba(255,255,255,0.8); font-size: 24rpx; margin-top: 10rpx; }
.list-section { margin-top: 20rpx; background: #fff; }
.item { 
	display: flex; justify-content: space-between; 
	padding: 30rpx 40rpx; border-bottom: 1rpx solid #eee; 
	font-size: 28rpx; color: #333;
}
.arrow { color: #ccc; }
</style>