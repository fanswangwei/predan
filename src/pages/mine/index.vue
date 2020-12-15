<template>
	<view class="page-mine">
		<view class="mine-info">
			<view class="mine-pic"></view>
			<text class="mine-name">mine-name</text>
		</view>
		<view class="mine-record">
			<view v-for="(item, index) in recordList" :key="index" class="record-item">
				<text class="title">捐赠记录</text>
				<view class="record-info">
					<view class="info-item">
						<text class="label">约定地点</text>
						<text class="info">上海市浦东新区唐镇福民路128号504</text>
					</view>
					<view class="info-item">
						<text class="label">上门时间</text>
						<text class="info">2020/12/24</text>
					</view>
					<view class="info-item">
						<text class="label">捐赠物品</text>
						<text class="info">图书</text>
					</view>
				</view>
				<image class="thanks" src="/static/images/thanks.png" mode="" />
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			recordList: [{}, {}],
		}
	},
	onLoad() {},
	methods: {
		
	},
}
</script>

<style lang="scss" scoped>
.page-mine {
	width: 100%;
	.mine-info {
		width: 100%;
		height: 214px;
		background: url('/static/images/mine.jpg') no-repeat;
		background-size: 100%;
		position: relative;
		.mine-pic {
			position: absolute;
			left: 16px;
			bottom: 46px;
			width: 60px;
			height: 60px;
			border-radius: 50%;
			background: #264151;
		}
		.mine-name {
			position: absolute;
			bottom: 46px;
			left: 95px;
			color: #ffffff;
			font-family: 'PingFang SC';
			font-size: 24px;
			font-weight: 600;
			line-height: 60px;
		}
	}
	.logo {
		width: 100%;
	}
	.title {
		font-family: 'PingFang SC';
		font-size: 18px;
		font-weight: 600;
		color: #666;
	}
	.mine-record {
		padding: 10px 15px;
		.record-item {
			margin-bottom: 18px;
			position: relative;
			.record-info {
				.info-item {
					overflow: hidden;
					margin-top: 5px;
					box-shadow: inset 0 -1px 0 0 #f7f7f7;
					text {
						float: left;
						color: #666666;
						font-family: 'PingFang SC';
						font-size: 14px;
						line-height: 40px;
					}
					.info {
						margin-left: 10px;
						font-weight: 500px;
					}
				}
			}
			.thanks {
				position: absolute;
				right: 5px;
				bottom: 5px;
				width: 70px;
				height: 70px;
			}
		}
	}
}
</style>
