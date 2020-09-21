<template>
	<view>
		<!-- <view class="infoimg"><image class="img" src="../../static/img/3.jpg"></image></view> -->
		<view class="uni-padding-wrap">
			<view class="page-section swiper">
				<view class="page-section-spacing">
					<swiper class="swiper">
						<swiper-item>
							<view class="swiper-item"><image src="../../static/img/3.jpg" class="swiperimg"></image></view>
						</swiper-item>
					</swiper>
				</view>
			</view>
		</view>
		<view class="flex-row">
			<view class="flex-left">
				<view class="left-icon blue"><text class="iconfont iconliulanqi"></text></view>
			</view>
			<view class="flex-center"><text>医院官网</text></view>
			<view class="flex-right">
				<text class="underline" @click="locaolWeb(web)">{{ web }}</text>
			</view>
		</view>

		<view class="flex-row">
			<view class="flex-left">
				<view class="left-icon green"><text class="iconfont icondianhua"></text></view>
			</view>
			<view class="flex-center"><text>医院电话</text></view>
			<view class="flex-right">
				<text class="underline" @click="call(tel)">{{ tel }}</text>
			</view>
		</view>

		<view class="flex-row">
			<view class="flex-left">
				<view class="left-icon yellow"><text class="iconfont icondizhi"></text></view>
			</view>
			<view class="flex-center"><text>医院地址</text></view>
			<view class="flex-right"><text>江苏省南京市宁六路219号</text></view>
		</view>

		<view class="flex-row">
			<view class="flex-left">
				<view class="left-icon darkblue"><text class="iconfont icongongjiao"></text></view>
			</view>
			<view class="flex-center"><text>乘车路线</text></view>
			<view class="flex-right">
				<text>{{ map }}</text>
			</view>
		</view>

		<view class="infodetails">
			<view class="gridTitle">
				<text class="titleicon">|</text>
				<text>医院简介</text>
			</view>
			<view class="details">
				南通，简称“通”，古称通州，别称静海、崇州、崇川，江苏省地级市，长江三角洲中心区27城之一 ，国务院批复确定的中国长三角北翼经济中心、现代化港口城市
				。截至2020年7月，全市辖3个区、1个县、代管3个县级市。总面积8001平方千米。常住人口731.8万人，城镇人口498.4万人，城镇化率67.1%。
				南通地处中国华东地区、江苏东南部，东抵黄海、南濒长江 ，是扬子江城市群的重要组成部分、上海大都市圈北翼门户城市、中国首批对外开放的14个沿海城市之一
				，集“黄金海岸”与“黄金水道”优势于一身，拥有长江岸线226千米，“据江海之会、扼南北之喉 ”，被誉为“北上海” 。
				南通是国家历史文化名城，自后周显德三年（956年）建城至今已有一千多年历史。在中国近代文化科教史上，南通创办第一所师范学校、第一座民间博物苑、第一所纺织学校、第一所刺绣学校、第一所戏剧学校、第一所中国人办的盲哑学校和第一所气象站等“七个第一”，被称为“中国近代第一城”。
				南通是“精神文明南通现象”的发源地 ，是中国、江苏省重大精神文明先进典型最多的地区之一 ，连续四次被评为全国文明城市 ，并先后入选国家智慧城市试点 、宽带中国示范城市 。
				截至2014年，南通人口平均预期寿命达80.71岁，百岁寿星多达1031位。 2014年5月，南通被国际自然医学会、世界长寿乡认证委员会授予全球首个“世界长寿之都”。
				2018年10月，获评首届健康中国年度标志城市。 2018年中国百强城市排行榜中，位列22位。
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			web: 'http://www.myrose.top/',
			tel: '0513-88888888',
			map: '市内乘D23、D16、201、204、221、222、252路 地铁S15到xxxxx站'
		};
	},
	methods: {
		locaolWeb(web) {
			window.location.href = web;
		},
		call(tel) {
			uni.makePhoneCall({
				// 手机号
				phoneNumber: tel,

				// 成功回调
				success: res => {
					console.log('调用成功!');
				},

				// 失败回调
				fail: res => {
					console.log('调用失败!');
				}
			});
		}
	}
};
</script>

<style scoped>
.infoimg {
	width: 100%;
	height: 170px;
}
.infoimg .img {
	width: 100%;
	height: 100%;
}
.flex-row {
	display: flex;
	flex-direction: row;
	flex-wrap: nowrap;
	justify-content: space-between;
	align-items: center;
	padding: 12px 20px;
	background-color: #ffffff;
	border-bottom: #f2f2f2 1px solid;
}
.left-icon {
	width: 33px;
	height: 33px;
	border-radius: 6px;
	text-align: center;
	display: table-cell;
	vertical-align: middle;
}
.flex-left {
	width: 50px;
}
.flex-center {
	width: 80px;
}
.flex-right {
	width: calc(100% - 130px);
	text-align: right;
}
.left-icon text {
	color: #ffffff;
	font-size: 24px;
}
.flex-center text {
	font-family: 'Arial Normal', Arial, sans-serif;
	font-weight: 400;
	font-size: 15px;
	color: #666666;
}
.flex-right text {
	font-family: 'Arial Normal', Arial, sans-serif;
	font-weight: 400;
	font-size: 14px;
	color: #999999;
	word-break: break-all;
}

.infodetails {
	font-family: 'Arial Normal', Arial, sans-serif;
	font-weight: bold;
	font-size: 15px;
	color: #1dbac2;
	background-color: #ffffff;
	margin-top: 10px;
}
.titleicon {
	color: #1dbac2;
	margin-right: 20rpx;
}

.gridTitle {
	padding: 20rpx 10rpx;
	/* font-size: 0.9rem; */
	font-size: 12px;
}
.details {
	padding: 0 10px 10px;
	color: #333333;
	font-weight: 400;
	font-size: 13px;
	word-break: break-all;
	text-indent: 1.5rem;
}
.underline{
	/* text-decoration: underline; */
	border-bottom: #999999 1px solid;
}
.blue{
	background-color: #7fcef5;
}
.green{
	background-color: #5cca8b;
}
.yellow{
	background-color: #feb12b;
}
.darkblue{
	background-color: #0099cc;
}
</style>
