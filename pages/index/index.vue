<template>
	<view>
		<view class="u-page">
			<!-- 所有内容的容器 -->
			<!-- <keep-alive></keep-alive> 缓存当前页面 -->
			<component v-bind:is="currentTabComponent"></component>
		</view>
		<!-- 与包裹页面所有内容的元素u-page同级，且在它的下方 -->
		<u-tabbar v-model="current" :list="list" active-color="rgb(80 152 255)" :mid-button="true"   :before-switch="beforeSwitch"></u-tabbar>
	</view>
</template>

<script>
	import cent from '../center/index.vue';
	import addMoney from '../addMoney/addMoney';
	import overview from '../overview/overview.vue';
	import my from '../my/my';
	import memorandum from '../memorandum/memorandum'
	export default {
		data() {
			return {
				// 初始化页面模板
				currentTabComponent: 'overview',
				// 下面是自定义底部table栏的每个list
				list: [{
						iconPath: "home",
						selectedIconPath: "home",
						text: '首页',
						customIcon: false,
					},
					{
						iconPath: "order",
						selectedIconPath: "order",
						text: '明细',
						customIcon: false
					},
					{
						iconPath: "https://cdn.uviewui.com/uview/common/min_button_select.png",
						selectedIconPath: "https://cdn.uviewui.com/uview/common/min_button_select.png",
						text: '添加',
						midButton: true,
						customIcon: false
					},
					{
						iconPath: "bookmark",
						selectedIconPath: "bookmark",
						text: '备忘录',
						customIcon: false,
					},
					{
						iconPath: "account",
						selectedIconPath: "account",
						text: '我的',
						customIcon: false,
					},
				],
				current: 0
			}
		},
		methods: {
			async beforeSwitch(index) {
				// 只能切换偶数项
				if (index == 0) {
					this.currentTabComponent = 'overview'
				} else if (index == 1) {
					this.currentTabComponent = 'cent'
				} else if (index == 2) {
					uni.navigateTo({
						url: '../addMoney/addMoney'
					});
				}else if(index == 3){
					this.currentTabComponent = 'memorandum'
				} else {
					this.currentTabComponent = 'my'
				}
			}
		},
		components: {
			cent,
			addMoney,
			overview,
			my,
			memorandum
		}
	}
</script>

<style lang="scss" scoped>

</style>
