<template>
	<view class="fullscreen">
		<view class="dayselect">
			<uni-grid :column="6" :show-border="false" :square="false">
				<uni-grid-item v-for="(item,i) in days" :key="i" :class="{ dayselected: i == current }">
					<view class="griditem" @click="chooseDate(i)">
						<view class="zhou">
							<text>周{{item.zhou}}</text>
						</view>
						<view class="day">
							<text>{{item.month}}.{{item.date}}</text>
						</view>
					</view>
				</uni-grid-item>
			</uni-grid>
		</view>
		<uni-segmented-control :current="current1" :values="items" @clickItem="onClickItem" style-type="text" active-color="#199ed8"></uni-segmented-control>
		<view class="content">
			<view v-if="current1 === 0">
				<view class="flex-row" v-for="(type1,j) in mztype1" :key="j" @click="gotoOrder(type1,1)">
					<view class="flex-left">
						<image :src="type1.img"></image>
					</view>
					<view class="flex-right">
						<text class="orsp1">{{type1.docName}}</text>
						<text class="orsp2">{{type1.docId}}</text>
						<text class="block orsp3">
							擅长：{{type1.chara}}
						</text>
					</view>
				</view>
			</view>
			<view v-if="current1 === 1">
				<view class="flex-row" v-for="(type2,h) in mztype2" :key="h" @click="gotoOrder(type2,2)">
					<view class="flex-left">
						<image :src="type2.img"></image>
					</view>
					<view class="flex-right">
						<text class="orsp1">{{type2.keshiName}}</text>
						<text class="block orsp3">
							科室特色：{{type2.chara}}
						</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				params: 'error', //接受上个页面传过来的科室信息
				current: 0,
				current1: 0,
				items: ['专家门诊', '普通门诊'], //内容选择器
				days: [],
				localObj: {},
				mztype1: [{
						img: '../../static/img/1.jpg',
						docName: '药无忌',
						docId: '主任医师',
						chara: '消化内镜常规开展胃镜、十二指肠、消化不良等'
					},
					{
						img: '../../static/img/2.jpg',
						docName: '药无忌',
						docId: '主任医师',
						chara: '消化内镜常规开展胃镜、十二指肠、消化不良等'
					},
					{
						img: '../../static/img/3.jpg',
						docName: '药无忌',
						docId: '主任医师',
						chara: '消化内镜常规开展胃镜、十二指肠、消化不良等'
					},
					{
						img: '../../static/img/4.jpg',
						docName: '药无忌',
						docId: '主任医师',
						chara: '消化内镜常规开展胃镜、十二指肠、消化不良等'
					}
				],
				mztype2: [{
						img: '../../static/img/keshi.png',
						keshiName: '外科',
						chara: '消化内镜常规开展胃镜、十二指肠、消化不良等'
					},
					{
						img: '../../static/img/keshi.png',
						keshiName: '内科',
						chara: '消化内镜常规开展胃镜、十二指肠、消化不良等'
					},
					{
						img: '../../static/img/keshi.png',
						keshiName: '血液科',
						chara: '消化内镜常规开展胃镜、十二指肠、消化不良等'
					},
					{
						img: '../../static/img/keshi.png',
						keshiName: '皮肤科',
						chara: '消化内镜常规开展胃镜、十二指肠、消化不良等'
					},
					{
						img: '../../static/img/keshi.png',
						keshiName: '耳鼻喉科',
						chara: '消化内镜常规开展胃镜、十二指肠、消化不良等'
					}
				],
			}
		},
		methods: {
			getDays(day) {
				// 获取当日及后几日的信息
				// params：day 想获取多少天就写多少
				var now = new Date();
				var nowTime = now.getTime();
				var oneDayTime = 24 * 60 * 60 * 1000;
				for (var i = 0; i < day; i++) {
					var showTime = nowTime + i * oneDayTime;
					var myDate = new Date(showTime);
					var year = myDate.getFullYear();
					var month = myDate.getMonth() + 1;
					if (month > 0 && month < 10) {
						month = '0' + month
					}
					var date = myDate.getDate();
					if (date > 0 && date < 10) {
						date = '0' + date
					}
					var str = '日一二三四五六'.charAt(myDate.getDay());
					this.days.push({
						year: year,
						month: month,
						date: date,
						zhou: str
					});
				}
			},
			chooseDate(i) {
				// 选择预约日期
				var v = this;
				v.current = i;
				v.current1 = 0;
			},
			onClickItem(e) {
				// 选择门诊类型
				if (this.current1 !== e.currentIndex) {
					this.current1 = e.currentIndex;
				}
			},
			setLocal(item, type) {
				var v = this;
				v.localObj = {};
				v.localObj['type'] = type;
				v.localObj['chara'] = item.chara;
				v.localObj['img'] = item.img;
				v.localObj['selectedTime'] = '';
				v.localObj['morning'] = {status:0,time:'11111'};
				v.localObj['afternoon'] = {status:0,time:'11111'};
				v.localObj['year'] = v.days[this.current].year;
				v.localObj['month'] = v.days[this.current].month;
				v.localObj['date'] = v.days[this.current].date;
				v.localObj['zhou'] = v.days[this.current].zhou;
				if (type === 1) {
					v.localObj['docName'] = item.docName;
					v.localObj['docId'] = item.docId;
				} else if (type === 2) {
					v.localObj['keshiName'] = item.keshiName;
				}

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
					uni.setStorageSync('order', JSON.stringify(v.localObj));
				} catch (e) {
					console.log('order缓存到本地错误');
				};
			},
			gotoOrder(item, type) {
				// 去预约界面
				var v = this;
				v.setLocal(item, type);
				uni.navigateTo({
					url: '../views/orderRegister3'
				})
			}
		},
		onLoad: function(params) {
			this.params = params.params;
			this.getDays(6);
		}
	}
</script>

<style scoped>
	page {
		height: 100%;
		background-color: #FFFFFF;
	}

	.dayselect {
		padding: 0 10px;
		text-align: center;
		color: #333333;
		border-bottom: #f2f2f2 1px solid;
	}

	.dayselected {
		color: #199ed8 !important;
	}

	.griditem {
		padding: 12px 0 6px 0;
	}

	.day {
		font-family: 'Arial Negreta', 'Arial', sans-serif;
		font-weight: 700;
		font-size: 16px;
	}

	.zhou {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-size: 14px;
		padding-bottom: 2px;
	}

	.content {
		height: calc(100% - 94px);
		overflow: auto;
	}

	.flex-row {
		padding: 10px 20px;
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		border-bottom: #F2F2F2 1px solid;
	}

	.flex-left {
		/* padding: 0 10px; */
		width: 50px;
		height: 50px;
		line-height: 50px;
		overflow: hidden;
		border-radius: 25px;
	}


	.flex-left image {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.flex-right {
		padding-left: 20px;
		width: calc(100% - 50px);
		height: 50px;
	}

	.orsp1 {
		font-family: "苹方 中等", 苹方, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 18px;
		color: #000000;
	}

	.orsp2 {
		display: inline-block;
		padding-left: 10px;
		font-family: "苹方 中等", 苹方, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #ff6600;
	}

	.orsp3 {
		padding-top: 10px;
		overflow: hidden;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 1;
	}
</style>
