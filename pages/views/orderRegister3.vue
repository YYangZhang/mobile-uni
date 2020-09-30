<template>
	<view class="fullscreen">
		<view class="content">
			<view class="flex-row">
				<view class="flex-left">
					<image :src="localObj.img" :class="localObj.type == '1' ? 'img1' : 'img2'"></image>
				</view>
				<view class="flex-right">
					<text class="orsp1" v-if="localObj.type == '1'">{{ localObj.docName }}</text>
					<text class="orsp4" v-if="localObj.type == '2'">{{ localObj.keshiName }}</text>
					<text class="orsp2">{{ localObj.docId }}</text>
					<text class="block orsp3">
						<text v-if="localObj.type == '1'">擅长：</text>
						<text v-if="localObj.type == '2'">科室特色：</text>
						{{ localObj.chara }}
					</text>
				</view>
			</view>
			<view class="content1">
				<view class="showtime">
					<text class="orsp5">
						就诊时间：
						<text class="orsp6">{{ localObj.year }}-{{ localObj.month }}-{{ localObj.date }} 星期{{ localObj.zhou }}</text>
					</text>
					<text class="orsp7">
						诊查费
						<text class="orsp8">{{ money }}</text>
						元
					</text>
				</view>
				<view class="morning">
					<text class="block">上午</text>
					<text class="block">(08:00——11:00)</text>
					<text class="block orsp20" v-show="morning.time == ''">{{['有号','没号'][morning.status]}}</text>
					<text class="block orsp20" v-show="morning.time != ''">{{morning.time}}</text>
					<text class="block orsp9" @click="open('0')">预约</text>
				</view>
				<view class="afternoon">
					<text class="block">下午</text>
					<text class="block">(13:00——16:00)</text>
					<text class="block orsp20" v-show="afternoon.time == ''">{{['有号','没号'][afternoon.status]}}</text>
					<text class="block orsp20" v-show="afternoon.time != ''">{{afternoon.time}}</text>
					<text class="block orsp9" @click="open('1')">预约</text>
				</view>
			</view>
			<view class="content1">
				<view class="flex-row1">
					<view class="flex-left1"><text>当前就诊人</text></view>
					<view class="flex-right1"><text class="orsp10" @click="changeUser()">切换就诊人</text></view>
				</view>
				<view class="content2">
					<view class="content3" v-show="!showUser">
						<text class="iconfont icontianjia block orsp11" @click="addUser"></text>
						<text class="block orsp12" >添加就诊人</text>
					</view>
					<view class="content3" v-show="showUser">
						<view class="orsp15">
							<text class="iconfont iconchenggong orsp14"></text>
							<view class="orsp13">
								<image src="../../static/img/1.jpg"></image>
							</view>
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
		<view class="footer">
			<view class="footer-left">
				<text>您已选择：<text>2017-07-03 {{localObj.selectedTime}}</text></text>
			</view>
			<view class="footer-right">
				确定预约
			</view>
		</view>
		<uni-popup ref="popup" type="bottom" :maskClick="false">
			<view class="popup1">
				<text class="block" style="padding-bottom: 20px;">选择就诊时间</text>
				<uni-icons type="closeempty" size="30" class="closeicon" @click="closePopup"></uni-icons>
				<view class="timearea">
					<text class="block orsp21" v-for="(item,idx) in times" :key="idx" @click="selectTime(item)">{{item}}</text>
				</view>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				sh: '', //测试
				toptitle: '', //头部标题
				money: '15.0',
				showUser: false, // false:当前就诊人列表为空或者无默认就诊人
				localObj: {}, // 上个页面存储到本地的信息
				morning: { //上午
					status: '', // 状态 是否有号 0为有 1为无
					time: '' // 选择时间
				},
				afternoon: { //下午
					status: '',
					time: ''
				},
				// selectedtime: '', //选中的时间
				selectedUser: '', //选中的就诊人
				noon: '', // 用来判断点击的预约为上午还是下午
				times: [],
				timeList1: [
					'08:00-08:30',
					'08:30-09:00',
					'09:00-09:30',
					'09:30-10:00',
					'10:00-10:30',
					'10:30-11:00',
				],
				timeList2: [
					'13:00-13:30',
					'13:30-14:00',
					'14:00-14:30',
					'14:30-15:00',
					'15:00-15:30',
					'15:30-16:00',
				]
			};
		},
		methods: {
			setTopTitle() {
				// 设置tarbar tiltle标题
				uni.setNavigationBarTitle({
					title: this.toptitle
				});
			},
			changeUser() {
				// 选择就诊人
				var v = this;
				uni.navigateTo({
					url: './patient/selectPatient'
				})
				v.setlocal();
				v.getlocal();
			},
			addUser() {
				// 添加就诊人
				uni.navigateTo({
					url: '../views/patient/editPatient?params=add'
				})
			},
			open(noon) {
				// 打开弹出框 
				var v = this;
				v.$refs.popup.open();
				v.noon = noon;
				if (noon == '0') {
					v.times = v.timeList1;
				} else if (noon == '1') {
					v.times = v.timeList2;
				}
			},
			closePopup() {
				// 关闭弹出框
				this.$refs.popup.close();
			},
			selectTime(value) {
				// 选择就诊时间
				var v = this;
				v.localObj.selectedTime = value;
				if (v.noon == '0') { //上午
					v.morning.time = value;
					v.afternoon.time = '';
				} else if (v.noon == '1') {
					v.afternoon.time = value;
					v.morning.time = '';
				}
				v.closePopup();
			},
			getlocal() {
				// 从本地缓存取出参数
				var v = this;
				v.localObj = {};
				try {
					v.localObj = JSON.parse(uni.getStorageSync('order'));
				} catch (e) {
					console.log('error');
				};
				v.morning = v.localObj.morning;
				v.afternoon = v.localObj.afternoon;
			},
			setlocal() {
				// 向本地缓存最新的参数
				// 同步获取 当前 storage 的相关信息
				// 判断 storage.keys中是否存在 order 若存在则删除
				try {
					const res = uni.getStorageInfoSync();
					if (res.keys.indexOf('order') > -1) {
						// 从本地缓存中 同步移除指定 order
						try {
							uni.removeStorageSync('order');
						} catch (e) {
							console.log('移除本地缓存order错误')
						}
					}
				} catch (e) {
					console.log('获取当前sotrage信息错误')
				};

				// 将localObj同步存放到本地 order
				try {
					uni.setStorageSync('order', JSON.stringify(this.localObj));
				} catch (e) {
					console.log('order缓存到本地错误');
				};
			}
		},
		onLoad() {
			this.getlocal();
			if (this.localObj.type == 1) {
				this.toptitle = '专家门诊';
			} else if (this.localObj.type == 2) {
				this.toptitle = '普通门诊';
			}
			this.setTopTitle();
			// 页面初始化的时候将值赋给userSelected
			// 如果未登录 就跳转到登录页面
			if (this.userSelected == '') {
				// 获取当前用户的默认就诊人
				// 如果没有默认就诊人显示添加页面
			} else {
				// 通过userSelected的值来查询就诊人
			}





			// 有默认就诊人则去调取默认就诊人的信息

			//判断从哪个页面进入，如果从选择联系人中进入则需要给联系人重新赋值
			// var pages = getCurrentPages();
			// var beforepage = pages[pages.length - 2];
			// console.log(beforepage.route);
			// if (beforepage.route == 'pages/views/orderRegister2') {
			// 	console.log('success')
			// }
		},
		//返回接收参数
		onShow: function() {
			console.log(this.sh)
		},
	};
</script>

<style scoped>
	page {
		height: 100%;
	}

	.content {
		height: calc(100% - 50px);
		overflow: auto;
	}

	.footer {
		height: 50px;
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;

	}

	.footer-left {
		width: calc(100% - 140px);
		background-color: #ffffff;
		text-align: center;
		height: 100%;
		color: #268EFD;
		/* line-height: 50px; */
		display: flex;
		justify-content: space-around;
		padding: 0 10px;
		word-break: break-word;

	}

	.footer-left text {
		align-self: center;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
	}

	.footer-left text text {
		font-size: 12px;

	}

	.footer-right {
		width: 140px;
		background-color: #268EFD;
		text-align: center;
		height: 100%;
		font-family: 'Arial Negreta', 'Arial', sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 16px;
		color: #FFFFFF;
		line-height: 50px;
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
		margin-bottom: 10px;
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

	.orsp16 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 16px;
		color: #000000;
		padding-top: 10px;
	}

	.orsp17 {
		padding-top: 20px;
	}

	.orsp18 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #000000;
	}

	.orsp19 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
		color: #666666;
		margin-left: 10px;
	}

	.orsp20 {
		text-align: center;
		width: 70px;
	}

	.popup1 {
		padding: 20px;
		text-align: center;
		background-color: #FFFFFF;
		border-radius: 10px 10px 0 0;
		position: relative;
		font-family: "Arial Negreta", Arial, sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 18px;
	}

	.closeicon {
		position: absolute;
		right: 10px;
		top: 10px;
	}

	.timearea {
		background-color: #FFFFFF;
		text-align: center;
		font-family: "微软雅黑 Regular", 微软雅黑, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #333333;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: flex-start;
		align-items: center;
		padding: 0 20px 0 20px;
		overflow: auto;
		min-height: 100px;
		max-height: 300px;

	}

	.orsp21 {
		width: 50%;
		padding: 6px;

	}
</style>
