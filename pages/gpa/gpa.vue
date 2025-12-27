<template>
	<view class="container">
		<view class="gpa-card">
			<text class="title">平均绩点 (GPA) 计算</text>
			<view class="course-row" v-for="(item, index) in courses" :key="index">
				<input class="input" type="digit" v-model.number="item.credit" placeholder="学分" />
				<input class="input" type="digit" v-model.number="item.score" placeholder="成绩" />
				<text class="del" @click="courses.splice(index, 1)">删除</text>
			</view>
			<button class="add-btn" @click="courses.push({credit:'', score:''})">+ 添加课程</button>
			<button class="calc-btn" @click="calculate">开始计算</button>
			<view v-if="result" class="res-box">结果：<text class="res-val">{{ result }}</text></view>
		</view>
	</view>
</template>

<script setup>
import { ref, reactive } from 'vue';
const courses = reactive([{ credit: '', score: '' }]);
const result = ref('');
const calculate = () => {
	let totalC = 0, totalP = 0;
	courses.forEach(c => {
		if(c.credit && c.score) {
			totalC += c.credit;
			let p = c.score >= 60 ? (c.score - 50) / 10 : 0;
			totalP += p * c.credit;
		}
	});
	result.value = totalC > 0 ? (totalP / totalC).toFixed(2) : '0.00';
};
</script>

<style scoped>
.container { padding: 30rpx; background: #f8f8f8; min-height: 100vh; }
.gpa-card { background: #fff; padding: 30rpx; border-radius: 20rpx; }
.title { font-size: 34rpx; font-weight: bold; color: #2d6a4f; margin-bottom: 30rpx; display: block; }
.course-row { display: flex; gap: 15rpx; margin-bottom: 20rpx; align-items: center; }
.input { border: 1rpx solid #eee; padding: 15rpx; flex: 1; border-radius: 8rpx; font-size: 26rpx; }
.del { color: #ff4d4f; font-size: 24rpx; width: 60rpx; }
.add-btn { margin-top: 30rpx; font-size: 26rpx; border: 1rpx solid #2d6a4f; color: #2d6a4f; background: none; }
.calc-btn { margin-top: 20rpx; background: #2d6a4f; color: #fff; }
.res-box { margin-top: 40rpx; text-align: center; font-size: 30rpx; }
.res-val { color: #2d6a4f; font-size: 50rpx; font-weight: bold; margin-left: 10rpx; }
</style>