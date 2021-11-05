<template>
	<view>
		<u-navbar back-icon-size="0" back-text="取消" title="记账" :border-bottom="false">
			<view slot='right' class="nav-right" @click="postFrom">完成</view>
		</u-navbar>
		<view class="content">
			<!-- 正文内容 -->
			<u-form :model="form" :error-type="errorType" ref="uForm">
				<u-form-item label="金额" prop="name">
					<u-input v-model="form.name" placeholder="请输入金额" input-align="right" :focus="true" />
				</u-form-item>
				<u-form-item label="日期" >
					<u-input v-model="form.showTime" placeholder="请选择日期" :disabled="true"   input-align="right" @click="show = true"
						 />
				</u-form-item>
				<u-form-item label="类型" prop="billType">
					<u-input v-model="form.billType"  :disabled="true"   input-align="right" @click="typeShow = true" />
				</u-form-item>
				<u-form-item label-position="top" :border-bottom='false' label="备注" >
					<u-input v-model="form.message"  :type="type" :border="border" :height="height" :auto-height="autoHeight" />
				</u-form-item>
			</u-form>
			<!-- 时间选择 -->
			<view>
				<!-- 时间 -->
				<u-picker v-model="show" @confirm="confirm"  mode="time"></u-picker>
				<!-- 类型 -->
				<u-select v-model="typeShow" mode="single-column" :list="list" @confirm="typeConfirm"></u-select>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg: '这是添加页面',
				form: {
					name: '',
					showTime: '今天'   ,//显示的时间
					postTime: new Date().getTime(), //真实提交的时间
					billType: '支出',
					message:''
				},
					list: [
						{
							value:'1',
							label: '支出'
						},
						{
							value:'2',
							label: '收入'
						}
					],
				show: false,
				typeShow:false,
				border: true,
				height: 100,
				autoHeight: true,
				type: 'textarea',
				rules: {
					name: [{
						required: true,
						message: '请输入金额',
						trigger: ['change', 'blur'],
					}]
				},
				errorType: ['toast'] //错误提示
			}
		},
		methods: {
			postFrom() {
				this.$refs.uForm.validate(valid => {
					if (valid) {
						console.log('金额:' + this.form.name)
						console.log('日期:' + this.form.postTime)
						console.log('类型:' + this.form.billType)
						console.log('备注:' + this.form.message)
						uni.navigateBack({
							delta:1
						})
						// console.log('验证通过');
					} else {
						console.log('验证失败');
					}
				});
			},
			// 时间回调
			confirm(e){
				this.form.showTime = e.year  + '-'  + e.month  + '-' + e.day;  //显示的时间
				this.form.postTime = e.timestamp  //真实的时间
			},
			// 类型选择回调
			typeConfirm(e){
				console.log(e[0].label)
				this.form.billType = e[0].label
			}
		},
		onReady() {
			this.$refs.uForm.setRules(this.rules);
		}
	
	}
	
	
</script>

<style scoped>
	.nav-right {
		margin-right: 30rpx;
	}

	.content {
		padding: 30rpx 20rpx 0;
	}

	.title {
		color: $u-type-primary;
		text-align: center;
		padding: 20rpx 0 0 0;
	}
</style>
