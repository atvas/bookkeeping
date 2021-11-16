<template>
	<view class="over-body">
		<u-navbar :is-back="false" :border-bottom="false" :background="bgColor" title-color="#ffffff"  title="账单"></u-navbar>
		<view class="head">
			<view class="head-nav">
				<view >
					<text @click="getTavList(0)" :class="{active:key == 0}">月账单</text>
				</view>
				<view>
					<text @click="getTavList(1)" :class="{active:key == 1}">年账单</text>
				</view>
			</view>
		</view>
		<view class="container">
			<component v-bind:is="pageTab"></component>
		</view>

	</view>
</template>

<script>
	import montglyBill from "./montglyBill"
	import annualBill from "./annualBill"
	var tis = new Date();  //初始化时间
	export default {
		data() {
			return {
				bgColor:{  //当前的状态栏的颜色
					backgroundColor: "#5098ff"
				},
				key: 0,
				pageTab:'montglyBill'
			}
		},
		methods: {
			getTavList(mKey){
				this.key = mKey  //动态修改样式
				if(mKey == 0){
					this.pageTab = "montglyBill"
				}else{
					this.pageTab = "annualBill"
				}
			}
		},
		components:{
			montglyBill,
			annualBill
		}
	}
</script>

<style>
	uni-page-wrapper{
		background-color: #FFFFFF;
	}
	.head{
		padding: 20rpx 0;
		background-color: #5098ff;
	}
	.head-nav{
		display: flex;
		justify-content: center;
	}
	.head-nav view{
		width: 25%;
		color: #FFFFFF; 
		text-align: center;
	}
	.active{
		border-bottom: 4rpx solid #FFFFFF;
	}
</style>
