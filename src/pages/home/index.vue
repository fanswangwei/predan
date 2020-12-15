<template>
	<view class="page-home">
		<view class="home-info">
			<image src="/static/images/home_index.jpg" mode="" />
		</view>
		<view class="planet-recycle">
			<text class="title">绿星回收</text>
			<view class="recycle-process">
				<view>
					<text>在线预约</text>
				</view>
				<text class="process-line"></text>
				<view>
					<text>免费上门</text>
				</view>
				<text class="process-line"></text>
				<view>
					<text>助力公益</text>
				</view>
			</view>
			<view class="recycle-book">
				<image src="/static/images/recycle-book.png" @click="pageJump('/pages/book/index')" />
			</view>
		</view>
		<view class="planet-donate">
			<text class="title">绿星捐赠</text>
			<view class="donate-category">
				<view class="clothes">
					<image src="/static/images/donate-clothes.png" @click="pageJump('/pages/clothes/index')" mode="" />
				</view>
				<view class="stationery">
					<image
						src="/static/images/donate-stationery.png"
						@click="pageJump('/pages/stationery/index')"
						mode=""
					/>
				</view>
			</view>
		</view>
		<view class="planet-status">
			<text class="title">绿星动态</text>
			<view class="stray-animals">
				<image src="/static/images/stray_animals.png" mode="" />
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {}
	},
	onLoad() {},
	methods: {
		pageJump(path) {
			uni.navigateTo({ url: path })
		},
	},
}
</script>

<style lang="scss" scoped>
.page-home {
	width: 100%;
	.home-info {
		width: 100%;
		height: 214px;
		// background: url('/static/images/home_index.jpg') no-repeat;
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
	.planet-recycle {
		width: 100%;
		padding: 10px 15px;
		box-sizing: border-box;
		background-color: #fff;
		.recycle-process {
			display: flex;
			align-items: center;
			justify-content: space-between;
			margin: 10px;
			> view {
				text {
					color: #666666;
					font-family: 'PingFang SC';
					font-size: 14px;
					letter-spacing: -0.17px;
					line-height: 26px;
				}
			}
			.process-line {
				box-sizing: border-box;
				height: 0;
				width: 45px;
				border-top: 2px dashed #7fb564;
			}
		}
		.recycle-book {
			text-align: center;
			image {
				height: 48px;
			}
		}
	}
	.planet-donate {
		background: #fff;
		padding: 10px 15px;
		border-top: 10px solid #f7f7f7;
		.donate-category {
			display: flex;
			align-items: center;
			justify-content: space-between;
			margin: 10px;
			margin-top: 18px;
			view {
				width: 163px;
				height: 100px;
				image {
					width: 100%;
					height: 100%;
				}
			}
			.clothes {
				margin-right: 8px;
			}
			.stationery {
				margin-left: 8px;
			}
		}
	}
	.planet-status {
		padding: 10px 15px;
		padding-top: 0;
		.stray-animals {
			height: 100px;
			margin: 10px;
			margin-top: 18px;
			image {
				width: 100%;
				height: 100%;
			}
		}
	}
}
</style>
