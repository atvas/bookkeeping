<template>
	<view>
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
				<view class="navList"  @click="setList">
					<text :class="{active:colorTab==0}">设置</text>
				</view>
				<view class="navList" @click="charts">
					<text :class="{active:colorTab==1}">图表</text>
				</view>
			</view>
		</view>
		<view class="countent">
			<component v-bind:is="pageTab"></component>
		</view>
	</view>
</template>

<script>
	import setList from "./setList";
	import chart from "./chart"
	export default {
		data() {
			return {
				src:"../../static/tou3.png",
				userName:"Penghui.Huang",
				message:"I like you better every day",
				pageTab: "setList", //动态切换显示组件
				colorTab : 0  //动态切换nav颜色
			}
		},
		beforeCreate() {
			 uni.request({
			 	url: "https://api.mcloc.cn/love/?type=json", //随机生成一句情话
			 	method :'GET',
			 	success:(res) => {
			 		console.log(res)
					this.message = res.data.data
			 	}
			 });
		  },
		methods: {
			setList(){
				this.pageTab = "setList",
				this.colorTab = 0 //动态切换颜色
			},
			charts(){
				this.pageTab = "chart",
				this.colorTab = 1 //动态切换颜色
			}
		},
		components:{
			setList,
			chart
		}
	}
</script>

<style lang="scss">
	.head{
		position: relative;
		padding: 40rpx;
		width: 100%;
		padding-bottom: 150rpx;
		margin-bottom: 40rpx;
		border-bottom-left-radius: 40rpx;
		border-bottom-right-radius: 40rpx;
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
		border-bottom-left-radius: 40rpx;
		border-bottom-right-radius: 40rpx;
	}
	.navList{
		display: inline-flex;
		align-items: center;
		justify-content: center;
		width: 50%;
		font-size: 30rpx;
		font-weight: bold;
		color: #7f8286;
	}
	.active{
		position: relative;
		color: #5098ff;
	}
	.active::before{
		position: absolute;
		bottom: -6rpx;
		width: 100%;
		height: 4rpx;
		left: 0px;
		content: '';
		border-bottom: 4rpx solid #5098ff;
	}
</style>
