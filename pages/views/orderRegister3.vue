<template>
	<view class="fullscreen">
		<view class="content">
			<view class="flex-row">
				<view class="flex-left"><image :src="item.img" :class="type == '1' ? 'img1' : 'img2'"></image></view>
				<view class="flex-right">
					<text class="orsp1" v-if="type == '1'">{{ item.docName }}</text>
					<text class="orsp4" v-if="type == '2'">{{ item.keshiName }}</text>
					<text class="orsp2">{{ item.docId }}</text>
					<text class="block orsp3">
						<text v-if="type == '1'">擅长：</text>
						<text v-if="type == '2'">科室特色：</text>
						{{ item.chara }}
					</text>
				</view>
			</view>
			<view class="content1">
				<view class="showtime">
					<text class="orsp5">
						就诊时间：
						<text class="orsp6">{{ day.year }}-{{ day.month }}-{{ day.date }} 星期{{ day.zhou }}</text>
					</text>
					<text class="orsp7">
						诊查费
						<text class="orsp8">{{ money }}</text>
						元
					</text>
				</view>
				<view class="morning">
					<text class="block">上午</text>
					<text class="block">(8:00——11:00)</text>
					<text class="block" style="width: 70px;">08:00-08:05</text>
					<text class="block orsp9">预约</text>
				</view>
				<view class="afternoon">
					<text class="block">下午</text>
					<text class="block">(13:00——16:00)</text>
					<text class="block" style="width: 70px;text-align: center;">有号</text>
					<text class="block orsp9">预约</text>
				</view>
			</view>
			<view class="content1">
				<view class="flex-row1">
					<view class="flex-left1"><text>当前就诊人</text></view>
					<view class="flex-right1"><text class="orsp10">切换就诊人</text></view>
				</view>
				<view class="content2">
					<!-- <view class="content3">
						<text class="iconfont icontianjia block orsp11"></text>
						<text class="block orsp12">添加就诊人</text>
					</view> -->
					<view class="content3">
						<view class="orsp15">
							<text class="iconfont iconchenggong orsp14"></text>
							<view class="orsp13"><image src="../../static/img/1.jpg"></image></view>
						</view>
						<text class="block orsp16">孙漂亮</text>
						<view class="orsp17">
							<text class="orsp18">身份证号</text>
							<text class="orsp19">3206********0254</text>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="footer"></view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			item: [], //科室或者医师的信息
			type: '', //门诊类型 专家门诊？普通门诊
			toptitle: '', //头部标题
			day: '', //选中的日期
			money: '15.0'
		};
	},
	methods: {
		setTopTitle() {
			uni.setNavigationBarTitle({
				title: this.toptitle
			});
		}
	},
	onLoad: function(params) {
		this.item = JSON.parse(decodeURIComponent(params.item));
		this.type = params.type;
		this.day = JSON.parse(decodeURIComponent(params.day));
		if (this.type == 1) {
			this.toptitle = '专家门诊';
		} else if (this.type == 2) {
			this.toptitle = '普通门诊';
		}
		this.setTopTitle();
	}
};
</script>

<style scoped>
page {
	height: 100%;
}

.content {
	height: calc(100% - 50px);
}

.footer {
	height: 50px;
	background-color: #0099cc;
}

.flex-row {
	display: flex;
	flex-direction: row;
	flex-wrap: nowrap;
	padding: 20px;
	background-color: #199ed8;
}

.flex-left {
	width: 50px;
	height: 50px;
	border-radius: 25px;
	overflow: hidden;
	border: #ffffff 1px solid;
	background-color: #d4e8fe;
	position: relative;
}

.flex-left image {
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%, -50%);
}

.flex-left .img1 {
	width: 100%;
	height: 100%;
}

.flex-left .img2 {
	width: 36px;
	height: 36px;
}

.flex-right {
	padding-left: 20px;
	width: calc(100% - 50px);
}

.orsp1 {
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 16px;
	color: #ffffff;
}

.orsp2 {
	display: inline-block;
	padding-left: 10px;
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 12px;
	color: #ffffff;
}

.orsp3 {
	padding-top: 10px;
	overflow: hidden;
	display: -webkit-box;
	-webkit-box-orient: vertical;
	-webkit-line-clamp: 1;
	color: #ffffff;
}

.orsp4 {
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 17px;
	color: #ffffff;
}

.content1 {
	margin-top: 8px;
	background-color: #ffffff;
	padding: 10px;
}

.showtime {
	padding-bottom: 10px;
	padding-left: 10px;
	border-bottom: 1px #ebebeb dashed;
}

.orsp5 {
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 14px;
	color: #333333;
}

.orsp6 {
	color: #258efb;
	font-weight: bold;
}

.orsp7 {
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 13px;
	color: #666666;
	margin-left: 14px;
}

.orsp8 {
	color: #cc0000;
}

.morning {
	padding: 30px 10px 10px;
	border-bottom: #ebebeb 1px solid;
}

.afternoon {
	padding: 10px 10px 20px;
}

.morning,
.afternoon {
	display: flex;
	flex-direction: row;
	flex-wrap: nowrap;
	justify-content: space-between;
	align-items: center;
}

.orsp9 {
	padding: 2px 14px;
	background-color: #169bd5;
	border-radius: 14px;
	color: #ffffff;
	font-size: 10px;
}
.flex-row1 {
	display: flex;
	flex-direction: row;
	flex-wrap: nowrap;
	align-items: center;
	padding: 10px;
}
.flex-left1 {
	width: 50%;
	text-align: left;
}
.flex-right1 {
	width: 50%;
	text-align: right;
}

.orsp10 {
	padding: 2px 6px;
	background-color: #ffffff;
	border-radius: 14px;
	font-size: 10px;
	border: #999999 1px solid;
	color: #666666;
}
.content2 {
	height: 140px;
	position: relative;
}
.content3 {
	text-align: center;
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%, -50%);
}
.orsp11 {
	font-size: 50px;
	color: #199ed8;
}
.orsp12 {
	padding-top: 20px;
	font-family: 'Arial Normal', 'Arial', sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 15px;
}
.orsp13 {
	width: 50px;
	height: 50px;
	border-radius: 25px;
	border: #c2defc 1px solid;
	line-height: 50px;
	overflow: hidden;
	z-index: 1;
}
.orsp13 image {
	width: 100%;
	height: 100%;
}
.orsp14 {
	position: absolute;
	right: 0px;
	bottom: 0px;
	color: #19ced9;
	z-index: 99;
}
.orsp15 {
	position: relative;
	width: 50px;
	margin: 0 auto;
}

.orsp16{
	font-family: 'Arial Normal', 'Arial', sans-serif;
	    font-weight: 400;
	    font-style: normal;
			font-size: 16px;
			color: #000000;
			padding-top: 10px;
}
.orsp17{
	padding-top: 20px;
}
.orsp18{
	font-family: 'Arial Normal', 'Arial', sans-serif;
	    font-weight: 400;
	    font-style: normal;
	    font-size: 12px;
			color: #000000;
}
.orsp19{
	font-family: 'Arial Normal', 'Arial', sans-serif;
	    font-weight: 400;
	    font-style: normal;
			font-size: 12px;
			color: #666666;
			margin-left: 10px;
}
</style>
