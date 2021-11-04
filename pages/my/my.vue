<template>
	<view class="head">
		<view class="personal">
			<view class="userImg">
				<u-avatar class="tou" size="200" :src="src"></u-avatar>
			</view>
			<view class="userName">
				<text>{{userName}}</text>
				<text>{{message}}</text>
			</view>
		</view>
		<view class="navTab">
			<view class="navList">
				<text>详细</text>
			</view>
			<view class="navList">
				<text>概览</text>
			</view>
			<view class="navList">
				<text>设置</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src:"../../static/tou3.png",
				userName:"Penghui.Huang",
				message:"I like you better every day"
			}
		},
		onLoad() {
			
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.head{
		position: relative;
		padding: 40rpx;
		width: 100%;
		height: 650rpx;
		border-bottom-left-radius: 30rpx;
		border-bottom-right-radius: 30rpx;
		background-color: #FFFFFF;
		box-shadow: 0 0 26px 0 rgba(0, 85, 204, 0.1);
	}
	.userImg{
		margin: 0 auto;
		margin-top: 100rpx;
		width: 200rpx;
		height: 200rpx;
		border-radius: 50%;
		box-shadow: 0 0 60rpx 20rpx  rgba(0, 85, 204, 0.1);
	}
	.tou{
		width: 100%;
		height: 100%;
	}
	.userName{
		display: inline-flex;
		flex-wrap: wrap;
		width: 100%;
		margin: 0 auto;
		text-align: center;
		margin-top: 40rpx;
	}
	.userName text{
		width: 100%;
		font-size: 35rpx;
		font-weight: bold;
		color:#4c4e51;
	}
	.userName text:nth-child(2){
		font-size: 20rpx;
		margin-top: 10rpx;
		color: #a9adb3;
	}
	.navTab{
		position: absolute;
		left: 0;
		bottom: 0;
		display: flex;
		width: 100%;
		height: 120rpx;
		border-bottom-left-radius: 30rpx;
		border-bottom-right-radius: 30rpx;
	}
	.navList{
		display: inline-flex;
		align-items: center;
		justify-content: center;
		width: 33.3%;
		font-size: 30rpx;
		font-weight: bold;
		color: #7f8286;
	}
</style>
