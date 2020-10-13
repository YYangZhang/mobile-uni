<template>
	<view>
		<!-- 轮播图 -->
		<view class="uni-padding-wrap">
			<view class="page-section swiper">
				<view class="page-section-spacing">
					<!-- indicator-dots // 是否显示swiper上的小圆点 -->
					<!-- autoplay // 自动播放是否开启 -->
					<!-- interval // 图片轮播间隔 -->
					<!-- duration // 图片轮播时动画过渡的时间 -->
					<swiper class="swiper" indicator-dots autoplay :interval="4000" :duration="1000">
						<swiper-item v-for="(item, idx) in imgList" :key="idx">
							<view class="swiper-item">
								<image :src="item.src" class="swiperimg"></image>
							</view>
						</swiper-item>
					</swiper>
				</view>
			</view>
		</view>
		<!-- 公告栏 -->
		<!-- single // true为单行 -->
		<!-- scrollable // 是否滚动 -->
		<uni-notice-bar :speed="50" showIcon="true" :scrollable="scrollable" single="true" :text="msg" backgroundColor="#ffffff"
		 color="#333333" style="margin-bottom: 0px;" @click="gotoMore('../views/notice')"></uni-notice-bar>

		<view class="gridTotal" v-for="(service,i) in serviceList" :key="i">
			<view class="gridTitle">
				<text class="titleicon">|</text>
				<text>{{service.title}}</text>
			</view>
			<view class="gridContent">
				<uni-grid :column="4" :show-border="false" :square="false">
					<uni-grid-item v-for="(item,j) in service.list" :key="j">
						<view class="itemtotal" @tap="gotoMore(item.url,item.text)">
							<view class="icondiv">
								<text class="iconfont" :class="item.icon"></text>
							</view>
							<text class="icontitle">{{item.text}}</text>
						</view>
					</uni-grid-item>
				</uni-grid>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgList: [{
					src: '../../static/img/1.jpg'
				}, {
					src: '../../static/img/2.jpg'
				}, {
					src: '../../static/img/3.jpg'
				}, {
					src: '../../static/img/4.jpg'
				}],
				msgList: [{
						msg: '这是noticeBar测试消息1'
					},
					{
						msg: '这是noticeBar测试消息2'
					},
					{
						msg: '这是noticeBar测试消息3'
					},
					{
						msg: '这是noticeBar测试消息4'
					}
				],
				scrollable: false,
				msg: '公告栏: ',
				serviceList: [{
						title: '门诊服务',
						list: [{
								icon: 'iconbiaoqian',
								text: '添加就诊人',
								url:'../views/patient/editPatient'
							}, {
								icon: 'iconorder',
								text: '预约挂号',
								url:'../views/orderRegister1'
							},
							{
								icon: 'iconfuwutai',
								text: '门诊缴费',
								url:'../views/pay/menzhenPay'
							},
							{
								icon: 'iconrenwuqingdan',
								text: '报告查询',
								url:'../views/report/reportSearch'
							},
							{
								icon: 'icon1',
								text: '门诊缴费记录',
								url:'../info/test'
							}
						],

					},
					{
						title: '住院服务',
						list: [{
								icon: 'iconzhuyuanqingdan',
								text: '住院清单查询',
								url:'../info/test'
							},
							{
								icon: 'iconbingchuang',
								text: '住院缴费',
								url:'../info/test'
							},

							{
								icon: 'iconpeizhitubiaosvg-',
								text: '住院缴费记录',
								url:'../info/test'
							},
						]
					},
					{
						title: '公共服务',
						list: [{
								icon: 'iconyiyuan',
								text: '医院介绍',
								url:'../info/test'
							},
							{
								icon: 'iconxinwen',
								text: '新闻动态',
								url:'../views/news'
							},
						]
					},
				]

			}
		},
		methods: {
			// test(){
			// 	uni.navigateTo({
			// 		url:"../info/test"
			// 	})
			// }
			gotoMore(url,msg) {
				if(url == '../views/patient/editPatient'){
					console.log(url)
					uni.navigateTo({
						url:url + '?params=' + 'add'
					})
				}else{
					uni.navigateTo({
						// url: "../info/test?params=" + msg,
						url:url + '?params=' + msg
					})
				}
				
			}

		},
		onLoad() {
			if (this.msgList.length <= 0) {

			} else if (this.msgList.length == 1) {
				this.msg += '\xa0\xa0';
				this.msg += this.msgList[0].msg
			} else {
				this.scrollable = true;
				this.msg = '';
				for (var i = 0; i < this.msgList.length; i++) {
					this.msg += this.msgList[i].msg
					this.msg += '\xa0\xa0\xa0\xa0\xa0\xa0\xa0\xa0\xa0\xa0\xa0\xa0\xa0\xa0\xa0\xa0';
				}
			}
		},

	}
</script>

<style scoped>

	/* 整体的div eg:门诊服务 */
	.gridTotal {
		background-color: #ffffff;
		/* margin-top:16rpx; */
	}

	.titleicon {
		color: #199ed8;
		margin-right: 20rpx;
	}

	.gridTitle {
		padding: 20rpx 10rpx;
		/* font-size: 0.9rem; */
		font-size: 12px;
		color: #999999;
	}

	.gridContent {
		padding: 0 20rpx;
	}

	.itemtotal {
		margin: 20rpx 0;
		text-align: center;
	}

	.icondiv {
		width: 2.8rem;
		height: 2.8rem;
		border-radius: 1.4rem;
		text-align: center;
		border: #cde9fd 1px solid;
		background-color: #eef8fe;
		margin: 0 auto;
		position: relative;
	}

	.icondiv .iconfont {
		font-size: 1.4rem;
		position: absolute;
		color: #29a1f7;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
	}

	.icontitle {
		margin-top: 10rpx;
		display: inline-block;
		font-size: 10px;
	}
</style>
