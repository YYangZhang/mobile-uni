<template>
	<view class="fullscreen">
		<view class="content">
			<view class="contentHeader">
				<view class="left">
					<text class="iconfont iconbingchuang1"></text>
				</view>
				<view class="right">
					<view style="padding-top: 6px;">
						<text class="rptsp1">住院预缴金</text>
					</view>
				</view>
			</view>
			<view class="contentBody">
				<view class="choosePatient flex">
					<view class="rptsp3">当前就诊人</view>
					<view class="rptsp4" @click="changeUser()">切换就诊人<uni-icons type="arrowright" size="14" style="color: #828282;"></uni-icons>
					</view>
				</view>
				<view class="patientInfo flex" style="color: #666666;">
					<view class="rptsp5">姓名</view>
					<!-- <view class="rptsp6">{{name}}</view> -->
					<view class="rptsp6">
						<input v-model="name" class="rptsp7" />
					</view>
				</view>
				<view class="patientInfo flex">
					<view class="rptsp5">住院号</view>
					<!-- <view class="rptsp6">{{idno}}</view> -->
					<view class="rptsp6">
						<input v-model="idno" placeholder="请输入住院号" class="rptsp7 rptsp8"/>
					</view>
				</view>
			</view>
		</view>
		<view class="footer">
			<button type="primary" class="primarybtn" @click="search">查询</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				idno:'',
				name:'',
			}
		},
		methods: {
			changeUser() {
				// 选择就诊人
				uni.navigateTo({
					url: '../patient/selectPatient'
				})
			},
			search(){
				uni.navigateTo({
					url: '../pay/zhuyuanOrderInfo'
				})
			}
		},
		onShow: function() {
			console.log(this.idno,this.name);
		},
	}
</script>

<style scoped>
	page {
		height: 100%;
	}

	.content {
		height: calc(100% - 60px);
		overflow: auto;
	}
	
	.footer {
		height: 60px;
		padding-top: 10px;
	}

	.contentHeader {
		height: 100px;
		background-color: #61a0ef;
		display: -webkit-flex;
		/* Safari */
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: center;
		padding: 20px 10px;
	}

	.left {
		width: 60px;
		border: #6db2fe 4px solid;
		height: 100%;
		padding: 4px;
		border-radius: 50%;
		position: relative;
		background-color: #FFFFFF;
		box-shadow: 0px -2px 10px #2990fc;
		;
	}

	.left text {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		color: #2a90fc;
		font-size: 28px;
		font-weight: bold;
	}

	.right {
		width: calc(100% - 60px);
		padding-left: 16px;
		color: #FFFFFF;
	}

	.rptsp1 {
		font-family: 'Arial Negreta', 'Arial', sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 16px;
	}


	.contentBody {
		padding: 14px 10px 20px;
		background-color: #FFFFFF;
	}

	.choosePatient {
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
	}

	.rptsp3 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 13px;
		color: #666666;
	}

	.rptsp4 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #333333;
	}

	.patientInfo {
		flex-direction: row;
		flex-wrap: nowrap;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 15px;
		padding-top: 10px;
		padding-left: 4px;
		color: #000000;
		align-items: center;
	}

	.rptsp5 {
		width: 80px;
	}

	.rptsp6 {
		width: calc(100% - 80px);
	}
	.rptsp7{
		font-size: 15px;
	}
</style>
