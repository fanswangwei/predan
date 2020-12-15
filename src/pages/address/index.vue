<template>
	<view class="page-address">
		<view class="address-list">
			<radio-group @change="radioChange" class="list-box">
				<label class="address-item" v-for="(item, index) in addressList" :key="index">
					<radio
						style="transform:scale(0.7)"
						:value="item.value"
						:checked="index === current"
						color="#008446"
					/>
					<text class="radio-label">{{ item.adress }}</text>
				</label>
			</radio-group>
		</view>
    <view class="add-address" @click="pageJump">
      <image src="/static/images/add_address.png"/>
    </view>
	</view>
</template>
<script>
export default {
	name: '',
	data() {
		return {
			addressList: [
				{
					value: 'adress1',
					adress: '上海市浦东新区唐镇福民路128号501',
				},
				{
					value: 'adress2',
					adress: '上海市浦东新区唐镇福民路128号502',
				},
				{
					value: 'adress3',
					adress: '上海市浦东新区唐镇福民路128号511',
				}
			],
			current: 0,
		}
	},
	created() {},
	methods: {
		radioChange(event) {
			for (let i = 0; i < this.addressList.length; i++) {
				if (this.addressList[i].value === event.target.value) {
					this.current = i
					break
				}
			}
    },
    pageJump(){
      uni.navigateTo({ url: '/pages/addAddress/index' })
    }
	},
}
</script>
<style lang="scss" scoped>
.page-address {
	.address-list {
		padding: 10px 15px;
    padding-bottom: 70px;
    box-sizing: border-box;
		.list-box {
			width: 100%;
			.address-item {
				display: block;
				width: 100%;
				line-height: 45px;
				box-shadow: inset 0 -1px 0 0 #f7f7f7;
				.radio-label {
					color: #666666;
					font-family: 'PingFang SC';
					font-size: 14px;
					font-weight: 500;
					line-height: 45px;
				}
			}
		}
	}
  .add-address {
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
