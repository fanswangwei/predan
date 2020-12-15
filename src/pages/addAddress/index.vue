<template>
	<view class="page-add-address">
		<view class="address-form">
			<view class="address-form-item">
				<text class="title">联系人</text>
				<input
					class="form-item-input"
					v-model="addressForm.contact"
					name="contact"
					placeholder="请输入联系人"
				/>
			</view>
			<view class="address-form-item">
				<text class="title">手机号码</text>
				<input class="form-item-input" v-model="addressForm.phone" name="phone" placeholder="请输入手机号码" />
			</view>
			<view class="address-form-item">
				<text class="title">所在地区</text>
				<input class="form-item-input" v-model="addressForm.area" name="area" placeholder="请输入所在地区" />
			</view>
			<view class="address-form-item">
				<text class="title">详细地址</text>
				<input
					class="form-item-input"
					v-model="addressForm.address"
					name="address"
					placeholder="请输入详细地址"
				/>
			</view>
		</view>
		<view class="form-submit" @click="formSubmit">
			<image src="/static/images/submit.png" />
		</view>
	</view>
</template>

<script>
export default {
	components: {},
	data: () => ({
		addressForm: {
			contact: '张三',
			phone: '',
			area: '',
			address: '',
		},
	}),
	computed: {},
	methods: {
		formSubmit: function(e) {
			console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
			uni.showModal({
				content: '表单数据内容：' + JSON.stringify(this.addressForm),
				showCancel: false,
			})
		},
		formReset: function(e) {
			console.log('清空数据')
		},
	},
	watch: {},

	// 页面周期函数--监听页面加载
	onLoad() {},
	// 页面周期函数--监听页面初次渲染完成
	onReady() {},
	// 页面周期函数--监听页面显示(not-nvue)
	onShow() {},
	// 页面周期函数--监听页面隐藏
	onHide() {},
	// 页面周期函数--监听页面卸载
	onUnload() {},
	// 页面处理函数--监听用户下拉动作
	onPullDownRefresh() {
		uni.stopPullDownRefresh()
	},
	// 页面处理函数--监听用户上拉触底
	onReachBottom() {},
	// 页面处理函数--监听页面滚动(not-nvue)
	/* onPageScroll(event) {}, */
	// 页面处理函数--用户点击右上角分享
	/* onShareAppMessage(options) {}, */
}
</script>

<style lang="scss" scoped>
.page-add-address {
	.title {
		font-family: 'PingFang SC';
		font-size: 18px;
		font-weight: 600;
		color: #666;
	}
	.address-form {
		padding: 10px 15px;
		padding-bottom: 70px;
		.address-form-item {
			input {
				height: 40px;
				margin: 10px 0;
				line-height: 40px;
				box-shadow: inset 0 -1px 0 0 #f7f7f7;
				color: #666666;
				font-family: 'PingFang SC';
				font-size: 14px;
			}
		}
	}
	.form-submit {
		padding: 10px 16px;
		background: #fff;
		position: fixed;
		bottom: 0;
		height: 68px;
		width: 100%;
		box-sizing: border-box;
		image {
			width: 100%;
			height: 48px;
		}
	}
}
</style>
