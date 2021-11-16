<template>
	<view>
		<view class="head">
			<view class="headTime">
				<text @click="getDataTime()"> {{times.realTime}}<u-icon name="arrow-down"></u-icon></text>
			</view>
		</view>
		
		
		
		<!-- 组件时间模块 -->
		<u-picker v-model="times.show" mode="time" @confirm="confirm" :params="times.params"></u-picker>
	</view>
</template>

<script>
	var currentTime  = new Date();  //初始化时间
	console.log(currentTime.getFullYear())
	export default {
		data() { 
			return {
				msg :'月账单',
				times :{
					show : false,  //是否显示时间选择器
					realTime : currentTime.getFullYear() + '-' + currentTime.getMonth()+1 ,
					params :{
						year :true,
						month :true,
						day:false
					}
				}
			}
		},
		methods: {
			getDataTime(){
				this.times.show = true
			},
			confirm(e){
				console.log(e)
				this.times.realTime = e.year + '-' + e.month;
			}
		}
	}
</script>

<style>
	.head{
		padding: 10rpx 20rpx 20rpx 20rpx;
		background-color: #5098ff;
	}
	.headTime text{
		color: #FFFFFF;
	}
	
</style>
