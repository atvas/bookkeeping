<template>
	<view>
		<view class="u-page">
			<!-- 所有内容的容器 -->
			<component v-bind:is="currentTabComponent"></component>
		</view>
		<!-- 与包裹页面所有内容的元素u-page同级，且在它的下方 -->
		<u-tabbar v-model="current" :list="list" :mid-button="true" :before-switch="beforeSwitch"></u-tabbar>
	</view>
</template>

<script>
	import cent from '../center/index.vue';
	import addMoney from '../addMoney/addMoney';
	import overview from '../overview/overview';
	import my from '../my/my'
	export default {
		data() {
			return {
				// 初始化页面模板
				currentTabComponent: 'overview',
				// 下面是自定义底部table栏的每个list
				list: [{
						iconPath: "home",
						selectedIconPath: "home-fill",
						text: '首页',
						customIcon: false,
					},
					{
						iconPath: "photo",
						selectedIconPath: "photo-fill",
						text: '明细',
						customIcon: false
					},
					{
						iconPath: "https://cdn.uviewui.com/uview/common/min_button.png",
						selectedIconPath: "https://cdn.uviewui.com/uview/common/min_button_select.png",
						text: '添加',
						midButton: true,
						customIcon: false
					},
					{
						iconPath: "play-right",
						selectedIconPath: "play-right-fill",
						text: '待定',
						customIcon: false,
					},
					{
						iconPath: "account",
						selectedIconPath: "account-fill",
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
					this.currentTabComponent = 'addMoney'
				}else if (index == 4) {
					this.currentTabComponent = 'my'
				}
			}
		},
		components: {
			cent,
			addMoney,
			overview,
			my
		}
	}
</script>

<style lang="scss" scoped>
	
</style>
