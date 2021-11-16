<template>
	<view>
		<u-cell-item icon="star" :icon-style="iconStyle" @click="open" title="个人信息"></u-cell-item>
		<u-cell-item icon="bookmark" :icon-style="iconStyle" @click="open" title="预算设置"></u-cell-item>
		<u-cell-item icon="order" :icon-style="iconStyle" @click="open" title="年度账单"></u-cell-item>
		<u-cell-item icon="setting" :icon-style="iconStyle" @click="open" title="设置"></u-cell-item>
		
		<!-- 静态弹出框 -->
		<u-modal v-model="show" :show-title="false"  :content="content"></u-modal>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				mess:"这是设置列表页",
				show: false,
				content: '暂未实现',
				iconStyle:{
					color:'#0055cc95'
				}
			}
		},
		methods: {
			open() {
				this.show = true;
			}
		}
	}
</script>

<style>

</style>
