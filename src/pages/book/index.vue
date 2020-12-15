<template>
	<view class="page-book">
		<view class="book-bg">
			<image src="/static/images/book.jpg" mode="" />
		</view>
		<view class="book-info">
			<view class="book-type">
				<text class="title">书本品类</text>
				<view class="type-box flex">
					<view :class="['type-item']" v-for="(item, index) in typeList" :key="index">
						<image :src="item.icon" :class="item.label" />
					</view>
				</view>
			</view>
			<view class="address-info">
				<text class="title">地址信息</text>
				<view class="address-detail" @click="pageJump('/pages/address/index')">请选择地址信息</view>
			</view>
			<view class="reserve-time">
				<text class="title">预约时间</text>
				<view class="select-time">
					<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
						<text class="select-time-detail">{{ date }}</text>
					</picker>
				</view>
			</view>
			<view class="estimate-num">
				<text class="title">预估重量</text>
				<view class="num-box flex">
					<view class="num-item" v-for="(item, index) in numList" :key="index" @click="selectedNum(index)">
						<image :src="item.url + '.png'" v-show="numSelectedIndex != index" />
						<image :src="item.url + '_selected.png'" v-show="numSelectedIndex == index" />
					</view>
				</view>
				<text class="books-tips">教材类书籍暂不回收哦～</text>
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
					label: 'schoolbag',
					icon: '/static/images/icon/schoolbag.png',
				},
				{
					label: 'pencil',
					icon: '/static/images/icon/pencil.png',
				},
				{
					label: 'pencil',
					icon: '/static/images/icon/pencil.png',
				},
			],
			numList: [
				{
					value: '5-20',
					url: '/static/images/icon/5_20',
				},
				{
					value: '20',
					url: '/static/images/icon/20',
				},
			],
			numSelectedIndex: 0,
			date: currentDate,
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
		selectedNum(index) {
			this.numSelectedIndex = index
		},
		pageJump(path) {
			uni.navigateTo({ url: path })
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
.page-book {
	width: 100%;
	.book-bg {
		width: 100%;
		height: 214px;
		// background: url('/static/images/book.jpg') no-repeat;
		// background-size: 100%;
		position: relative;
		image {
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 214px;
		}
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
	.book-info {
		padding: 10px 15px;
		padding-bottom: 70px;
		> view {
			margin-bottom: 15px;
		}
		.book-type {
			.type-box {
				width: 70%;
				margin: 0 auto;
				margin-top: 15px;
				.type-item {
					image {
						height: 65px;
						&.schoolbag {
							width: 35px;
						}
						&.pencil {
							width: 55px;
						}
					}
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
		.estimate-num {
			.num-box {
				margin-top: 15px;
				.num-item {
					width: calc(50% - 10px);
					height: 50px;
					image {
						width: 100%;
						height: 100%;
					}
				}
			}
			.books-tips {
				color: #a6acb8;
				font-family: 'PingFang SC';
				font-size: 10px;
				font-weight: 500;
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
