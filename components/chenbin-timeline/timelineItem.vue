<template>
	<view class="timelineItem">
		<view class="timeItem">
			<view class="line">
				<view class="out" :style="{background: color == '' ? '' : color}">
					<view class="inner" :style="{background: color == '' ? '' : color}"></view>
				</view>
			</view>
			<view class="rightContent">
				<view class="leftTime">
					{{leftTime}}
				</view>
				<slot></slot>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		props: {
			leftTime: {
				type: String,
				default: ''
			},
			color: {
				type: String,
				default: ''
			}
		},
		data() {
			return {

			}
		}
	}
</script>

<style scoped lang="less">
	.timelineItem {
		.timeItem {
			display: flex;
			// border: red 1px solid;
			padding-top: 2px;
			.line:not(:last-child) {
				width: 1px;
				background: rgba(204, 204, 204, 1);
				position: relative;

				.out {
					position: absolute;
					top: 0;
					left: 50%;
					transform: translateX(-50%);
					display: flex;
					justify-content: center;
					align-items: center;
					width: 28rpx;
					height: 28rpx;
					background: #258dfc;
					border-radius: 50%;

					.inner {
						width: 18rpx;
						height: 18rpx;
						background: #258dfc;
						border-radius: 50%;
					}
				}
			}

			.rightContent {
				flex: 1;
				padding: 0 6rpx 20rpx 10rpx;
				margin-left: 20rpx;
				min-height: 50rpx;
				.leftTime {
					// width: 400rpx;
					padding: 0 10rpx;
					font-size: 28rpx;
					font-family: PingFangSC-Medium, PingFang SC;
					font-weight: 500;
					color: rgba(51, 51, 51, 1);
					margin-left: 10rpx;
					overflow: hidden;
					text-overflow: ellipsis;
					white-space: nowrap;
					padding-left: 10px;
					position: relative;
					top: -3px;
					margin-bottom: 20rpx;
				}
			}
		}
	}
</style>
