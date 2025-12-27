<template>
	<view class="container">
			<swiper 
			      class="banner" 
			      indicator-dots 
			      autoplay 
			      circular 
			      indicator-active-color="#2d6a4f"
			    >
			      <swiper-item v-for="item in banners" :key="item.id">
			        <image 
			          :src="item.url" 
			          mode="widthFix" 
			          class="banner-img"
			        ></image>
			      </swiper-item>
			    </swiper>

		<view class="section-title">最新公告</view>

		<view class="news-list">
			<view class="news-item" v-for="item in newsList" :key="item.id">
				<image :src="item.cover" mode="aspectFit" class="news-cover"></image>
				<view class="news-info">
					<text class="news-title">{{ item.title }}</text>
					<text class="news-date">{{ item.date }}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup>
import { ref } from 'vue';

// 在这里为每条新闻指定不同的图片路径
const newsList = ref([
	{ 
		id: 1, 
		title: '江西农业大学 120 周年校庆筹备工作启动', 
		date: '2025-12-25',
		cover: '/static/new1.png' 
	},
	{ 
		id: 2, 
		title: '关于 23 级数字媒体技术专业实训通知', 
		date: '2025-12-24',
		cover: '/static/new2.png' 
	},
	{ 
		id: 3, 
		title: '本周教学区空教室开放情况汇总', 
		date: '2025-12-23',
		cover: '/static/new1.png' 
	}
]);
// 定义轮播图数组，方便后续增加或减少图片
const banners = ref([
  { id: 1, url: '/static/banner1.png' },  
  { id: 2, url: '/static/banner2.jpg' }, 
  { id: 3, url: '/static/banner3.jpg' }  
]);


const handleCollect = () => {
	uni.showToast({
		title: '功能开发中...',
		icon: 'none',
		duration: 2000
	});
};

</script>

<style scoped>
.container { background: #f8f8f8; min-height: 100vh; padding-bottom: 30rpx; }
.banner { height: 350rpx; background: #eee; }
.banner-img { width: 100%; height: 100%; }

.section-title { padding: 30rpx; font-weight: bold; font-size: 32rpx; color: #2d6a4f; border-left: 10rpx solid #2d6a4f; margin: 20rpx 0; background: #fff; }

/* 新闻列表样式 */
.news-item { 
	background: #fff; margin: 0 20rpx 20rpx; padding: 20rpx; 
	border-radius: 16rpx; box-shadow: 0 4rpx 12rpx rgba(0,0,0,0.05); 
	display: flex; /* 开启 Flex 布局 */
	align-items: center;
}
/* 左侧缩略图样式 */
.news-cover { 
	width: 160rpx; height: 120rpx; border-radius: 8rpx; 
	margin-right: 20rpx; background: #f0f0f0; 
}
/* 右侧文字区域样式 */
.news-info { flex: 1; display: flex; flex-direction: column; justify-content: space-between; height: 120rpx; }
.news-title { font-size: 28rpx; color: #333; line-height: 1.4; font-weight: 500; display: -webkit-box; -webkit-box-orient: vertical; -webkit-line-clamp: 2; overflow: hidden; }
.news-date { font-size: 24rpx; color: #999; }
</style>