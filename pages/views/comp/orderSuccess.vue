<template>
	<view class="fullscreen">
		<view class="ordsuctop">
			<view class="finished">
				<view class="content1 contentbottom">
					<text class="iconfont iconchenggong"></text>
					<text class="block finsp1">预约成功，待支付</text>
				</view>
				<view class="content3 contentbottom">
					<view class="flex-row finpadbot">
						<view class="flex-left">
							<text class="finsp3">就诊序号：</text>
						</view>
						<view class="flex-right">
							<text class="finsp3">{{jzidx}}</text>
						</view>
					</view>
					<view class="flex-row finpadbot">
						<view class="flex-left">
							<text class="finsp3">就诊时间：</text>
						</view>
						<view class="flex-right">
							<text class="finsp3">{{jztime}}</text>
						</view>
					</view>
					<view class="flex-row">
						<view class="flex-left">
							<text class="finsp3">就诊地点：</text>
						</view>
						<view class="flex-right">
							<text class="finsp3">{{jzaddress}}</text>
						</view>
					</view>
				</view>
				<view class="content4 contentbottom">
					<view class="flex-row finpadbot2">
						<view class="flex-left">
							<text class="finsp4">科室：</text>
						</view>
						<view class="flex-right">
							<text class="finsp4">{{keshi}}</text>
						</view>
					</view>
					<view class="flex-row">
						<view class="flex-left">
							<text class="finsp4">门诊类型：</text>
						</view>
						<view class="flex-right">
							<text class="finsp4">{{mztype}}</text>
						</view>
					</view>
				</view>


				<view class="content4 contentbottom">
					<view class="flex-row finpadbot2">
						<view class="flex-left">
							<text class="finsp3">挂号费：</text>
						</view>
						<view class="flex-right">
							<text class="finsp5">￥ {{jzpay}}</text>
						</view>
					</view>
					<view class="flex-row">
						<view class="flex-left">
							<text class="finsp3">状态：</text>
						</view>
						<view class="flex-right">
							<text class="finsp3">{{status}}</text>
						</view>
					</view>
				</view>


				<view class="content4">
					<view class="flex-row finpadbot2">
						<view class="flex-left">
							<text class="finsp4">就诊人：</text>
						</view>
						<view class="flex-right">
							<text class="finsp4">{{jzname}}</text>
						</view>
					</view>
					<view class="flex-row">
						<view class="flex-left">
							<text class="finsp4">提交时间：</text>
						</view>
						<view class="flex-right">
							<text class="finsp4">{{subtime}}</text>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="ordsuctfoot">
			<view class="ordsuctfoot-left" @click="cancel">
				取消预约
			</view>
			<view class="ordsuctfoot-right" @click="gotopay">
				立即支付￥{{jzpay}}
			</view>
		</view>
		<!-- <uni-popup ref="popup" type="dialog">
		    <uni-popup-dialog type="dialog" message="成功消息" :duration="2000" :before-close="true" @close="close" @confirm="gotocancel"></uni-popup-dialog>
		</uni-popup> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				jzidx: "15",
				jztime: "2020/09/21 周二 上午",
				jzaddress: "门诊四楼东",
				keshi: "消化内科",
				mztype: "专家门诊 齐天大圣",
				jzpay: "10",
				status: "待挂号",
				jzname: "张无忌",
				subtime: "2020/09/20 15:10:10"
			}
		},
		methods: {
			cancel(){
				// 取消预约
				this.$refs.popup.open()
			},
			gotocancel(){
				// 跳转到取消成功页面
				uni.navigateTo({
					url:'pages/views/comp/canceled'
				})
			},
			gotopay(){
				// 去支付页面，跳转到挂号成功
				uni.navigateTo({
					url:'/pages/views/comp/registerSuccess'
				})
			}
		}
	}
</script>

<style scoped>
	page {
		height: 100%;
	}

	.finished {
		background-color: #FFFFFF;
		border-radius: 10px;
		border: #e4e4e9 1px solid;
		padding: 0 4px;
		/* box-shadow: 1px 1px 1px #e4e4e9; */
	}

	.content1,
	.content3,
	.content4 {
		padding: 16px 10px;
	}

	.content1 {
		position: relative;
		text-align: center;
	}

	.content1 .iconchenggong {
		position: absolute;
		left: 50%;
		transform: translateX(-50%);
		top: -18px;
		font-size: 30px;
		color: #268efc;
	}

	.content1 .finsp1 {
		font-family: "Arial Negreta", Arial, sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 20px;
		padding: 10px 0 6px;
		color: #268efc;
	}

	.flex-row {
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: flex-end;
	}

	.flex-left {
		text-align: left;
	}

	.flex-right {
		text-align: right;
	}

	.finsp3 {
		font-family: "Arial Negreta", Arial, sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 15px;
		/* line-height: 30px; */
	}

	.finsp4 {
		font-family: "Arial Normal", Arial, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #999999;
	}

	.finpadbot {
		padding-bottom: 18px;
	}

	.finpadbot2 {
		padding-bottom: 6px;
	}

	.ordsuctop {
		height: calc(100% - 50px);
		padding: 30px 10px;
		overflow: auto;
	}

	.ordsuctfoot {
		height: 50px;
		display: flex;
		flex-wrap: nowrap;
		flex-direction: row;
		align-items: center;
	}

	.ordsuctfoot-left {
		font-family: 'Arial Negreta', 'Arial', sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 16px;
		color: #268EFD;
		height: 50px;
		width: 35%;
		text-align: center;
		background-color: #FFFFFF;
		line-height: 50px;
	}

	.ordsuctfoot-right {
		width: 65%;
		font-family: 'Arial Negreta', 'Arial', sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 16px;
		color: #FFFFFF;
		height: 50px;
		text-align: center;
		background-color: #268efd;
		line-height: 50px;
	}
	.finsp5{
		font-family: "Arial Negreta", Arial, sans-serif;
		    font-weight: 700;
		    font-style: normal;
		    font-size: 20px;
			color: #cc3300;
	}
</style>
