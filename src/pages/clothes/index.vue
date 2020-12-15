<template>
	<view class="page-clothes">
		<view class="clothes-bg"> </view>
		<view class="clothes-info">
			<view class="clothes-type">
				<text class="title">衣物品类</text>
				<view class="type-box flex">
					<view :class="['type-item']" v-for="(item, index) in typeList" :key="index">{{ item.label }}</view>
				</view>
			</view>
			<view class="address-info">
				<text class="title">地址信息</text>
				<view class="address-detail">请选择地址信息</view>
			</view>
			<view class="reserve-time">
				<text class="title">预约时间</text>
				<view class="select-time">
					<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
						<text class="select-time-detail">{{ date }}</text>
					</picker>
				</view>
			</view>
			<view class="estimate-kg">
				<text class="title">预估重量</text>
				<view class="kg-box flex">
					<view class="kg-item" v-for="(item, index) in kgList" :key="index" @click="selectedKg(index)">
						<image :src="item.url + '.png'" v-show="kgSelectedIndex != index" />
						<image :src="item.url + '_selected.png'" v-show="kgSelectedIndex == index" />
					</view>
				</view>
			</view>
		</view>
		<view class="selected-reserve">
			<image src="/static/images/selected_reserve.png" />
		</view>
	</view>
</template>

<script>
export default {
	data() {
		const currentDate = this.getDate({
			format: true,
		})
		return {
			typeList: [
				{
					label: '衣服',
					icon: ''
				},
				{
					label: '裤子',
					icon: ''
				},
				{
					label: '鞋子',
					icon: ''
				},
				{
					label: '帽子',
					icon: ''
				}
			],
			kgList: [
				{
					value: '5-10',
					url: '/static/images/icon/5_10kg'
				},
				{
					value: '10-20',
					url: '/static/images/icon/10_20kg'
				},
				{
					value: '20-30',
					url: '/static/images/icon/20_30kg'
				},
				{
					value: '30',
					url: '/static/images/icon/30kg'
				}
			],
			kgSelectedIndex: 0,
			date: currentDate
		}
	},
	onLoad() {},
	computed: {
		startDate() {
			return this.getDate('start')
		},
		endDate() {
			return this.getDate('end')
		},
	},
	methods: {
		selectedKg(index) {
			this.kgSelectedIndex = index
		},
		bindDateChange(e) {
			console.log(e.target.value)
			this.date = e.target.value
		},
		getDate(type) {
			const date = new Date()
			let year = date.getFullYear()
			let month = date.getMonth() + 1
			let day = date.getDate()

			if (type === 'start') {
				year = year - 0
			} else if (type === 'end') {
				year = year + 99
			}
			month = month > 9 ? month : '0' + month
			day = day > 9 ? day : '0' + day
			return `${year}-${month}-${day}`
		},
	},
}
</script>

<style lang="scss" scoped>
.page-clothes {
	width: 100%;
	.clothes-bg {
		width: 100%;
		height: 214px;
		background: url('/static/images/clothes.jpg') no-repeat;
		background-size: 100%;
		position: relative;
	}
	.title {
		font-family: 'PingFang SC';
		font-size: 18px;
		font-weight: 600;
		color: #666;
	}
	.flex {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	.clothes-info {
		padding: 10px 15px;
		> view {
			margin-bottom: 15px;
		}
		.clothes-type {
			.type-box {
				margin-top: 15px;
				.type-item {
					width: 20%;
					height: 80px;
					text-align: center;
					line-height: 80px;
					color: #666;
					font-size: 14px;
					font-weight: 300;
				}
			}
		}
		.address-info {
			.address-detail {
				margin-top: 15px;
				height: 40px;
				box-shadow: inset 0 -1px 0 0 #f7f7f7;
				color: #666;
				font-size: 14px;
				font-weight: 300px;
				line-height: 40px;
			}
		}
		.reserve-time {
			.select-time {
				margin-top: 15px;
				height: 40px;
				box-shadow: inset 0 -1px 0 0 #f7f7f7;
				.select-time-detail {
					color: #666;
					font-size: 14px;
					font-weight: 300px;
					line-height: 40px;
				}
			}
		}
		.estimate-kg {
			.kg-box {
				margin-top: 15px;
				.kg-item {
					width: 80px;
					height: 80px;
					image {
						width: 100%;
						height: 100%;
					}
				}
			}
		}
	}
	.selected-reserve {
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
