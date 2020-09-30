<template>
	<view class="fullscreen">
		<view v-show="!usershow" class="none">
			<view class="imgdiv">
				<image src="../../../static/img/2.jpg"></image>
			</view>
			<text>您尚未添加就诊人，请先添加哦</text>
			<button type="primary" size="default" class="primarybtn" @click="gotoEdit('add')" style="margin-top: 80px;">添加就诊人</button>
		</view>
		<view v-show="usershow" class="newpage">
			<!-- <view class="users">
				<view class="user" v-for="(item,index) in userlist" :key="index">
					<view class="usercard">
						<view class="userInfo">
							<text>{{item.name}}</text>
							<view>身份证号：{{item.idno}}</view>
						</view>
						<view class="userEdit">
							<text class="iconfont iconbianji" style="color: #02c9bf;font-size: 40px;" @click="gotoEdit('edit','userid')"></text>
						</view>
					</view>
					<view style="padding-top: 6px;">
						<label @click="radioSelect(index)" :class="item.checked?'textblue':''">
							<radio value="item.checked" :checked="item.checked" class="form-radio" />{{item.checked?'默认就诊人':'设为默认就诊人'}}</label>
					</view>
				</view>
			</view> -->
			<view class="users">
				<view class="user rowflex" v-for="(item,index) in userlist" :key="index" :class="item.default == '0'?'default':''">
					<radio :value="item.idno" :checked="checked" class="form-radio" style="width: 20px;display: block;" @click="gotolast(index)" />
					<view class="usercard" @click="gotolast(index)">
						<view class="userInfo">
							<text><text class="iconfont iconyonghu" style="color:#f38321;margin-right: 6px;font-size: 16px;"></text>{{item.name}}</text>
							<view>身份证号：{{item.idno}}</view>
						</view>
						<view class="userEdit">
							<text class="iconfont iconbianji" style="color: #02c9bf;font-size: 40px;" @click="gotoEdit('edit','userid')"></text>
						</view>
					</view>
					<text class="defaulttxt textblue" v-if="item.default == '0'">默认就诊人</text>
				</view>

			</view>
			<view class="newpagebtn">
				<button type="primary" size="default" class="regularbtn" @click="gotoEdit('add','userid')">添加就诊人</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userlist: [{
						name: '孙漂亮',
						idno: '320683********0311',
						checked: true,
						default: '0'
					},
					{
						name: '小可爱',
						idno: '320683********0311',
						checked: false,
						default: '1'
					},
					{
						name: '双枪老太婆',
						idno: '320683********0311',
						checked: false,
						default: '1'
					},
					{
						name: '无敌胖胖',
						idno: '320683********0311',
						checked: false,
						default: '1'
					},
					{
						name: '懒羊羊',
						idno: '320683********0311',
						checked: false,
						default: '1'
					}
				],
				usershow: false,
				value: 'a',
			}
		},
		methods: {
			getUserlist() {
				var v = this;
				// 如果 userlist 长度为 0 则显示添加就诊人页面
				if (v.userlist.length == 0) {
					v.usershow = false;
				} else {
					v.usershow = true;
				}
			},
			gotoEdit(type, id) {
				// type 为状态，add 为添加  edit 为编辑
				uni.navigateTo({
					url: "/pages/views/patient/editPatient?params=" + type + '&id=' + id,
				})
			},
			gotolast(index) {
				//判断从哪个页面进入，点击后返回该页面
				 var pages = getCurrentPages();
				 var prevPage = pages[pages.length - 2]; //上一个页面
				 //uni或者vue用$vm
				 prevPage.$vm.sh = this.userlist[index].idno,
				 uni.navigateBack({//返回
				 delta: 1
				 })
			},
			radioSelect(index) {
				var v = this;
				for (var i = 0; i < v.userlist.length; i++) {
					v.userlist[i].checked = false;
				}
				v.userlist[index].checked = true;
				v.getUserlist();
			}

		},
		onLoad() {
			// 页面初始化时获取该用户的 userlist 列表
			var v = this;
			v.getUserlist();

		}
	}
</script>

<style scoped>
	.none {
		text-align: center;
	}

	.imgdiv {
		margin: 60px auto;
		width: 180px;
		height: 160px;
		overflow: hidden;
	}

	.imgdiv image {
		width: 100%;
		height: 100%;
	}

	.none text {
		font-family: 微软雅黑, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 16px;
		color: #666666;

	}

	page {
		height: 100%;

	}

	.fullscreen {
		height: 100%;
	}

	.newpage {
		height: 100%;
	}

	.users {
		height: calc(100% - 80px);
		overflow: auto;
		padding: 10px 20px 0 20px;
	}

	.user {
		padding-top: 10px;
		justify-content: space-between;
		align-items: center;
	}

	.newpagebtn {
		height: 80px;
		padding-top: 20px;
	}

	.usercard {
		display: flex;
		flex-wrap: nowrap;
		flex-direction: row;
		padding: 16px 12px;
		/* border: #007AFF 1px solid; */
		width: calc(100% - 30px);
		border-radius: 10px;
		justify-content: center;
		background-color: #FFFFFF;
	}

	.userInfo {
		width: calc(100% - 40px);
	}

	.userInfo text {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 16px;
		color: #333333;
	}

	.userInfo view {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #666666;
		padding-top: 10px;
	}

	.userEdit {
		width: 40px;
		display: flex;
		align-items: center;
	}

	.form-radio {
		transform: scale(0.7);
		width: 30px;
		display: block;
	}

	.textblue {
		color: #4379ee;
	}

	.default {
		position: relative;
		padding-bottom: 20px;
	}

	.defaulttxt {
		position: absolute;
		left: 43px;
		bottom: 0px;
	}
</style>
