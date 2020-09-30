<template>
	<view>
		<form @submit="formSubmit" @reset="formReset">

			<view style="padding: 0 10px 40px 10px;background-color: #FFFFFF;">

				<view class="uni-form-item uni-column">
					<view class="title">关系</view>
					<view class="content">
						<picker @change="relationChange" :value="form.relation" name="relation" :range="relation">
							<view class="uni-input">{{relation[form.relation]}}</view>
						</picker>
						<uni-icons type="arrowdown" class="arrowdown" size="16"></uni-icons>
					</view>
				</view>

				<view class="uni-form-item uni-column">
					<view class="title">姓名</view>
					<view class="content">
						<input class="uni-input" name="name" placeholder="必填" :disabled="type == 'edit'" />
					</view>
				</view>

				<view class="uni-form-item uni-column">
					<view class="title">身份证号</view>
					<view class="content">
						<input class="uni-input" name="idcard" placeholder="必填" :disabled="type == 'edit'" type="idcard" />
					</view>

				</view>

				<view class="uni-form-item uni-column">
					<view class="title">卡类型</view>
					<view class="content">
						<picker @change="cardTypeChange" :value="form.cardType" name="cardType" :range="array">
							<view class="uni-input">{{array[form.cardType]}}</view>
						</picker>
						<uni-icons type="arrowdown" class="arrowdown" size="16"></uni-icons>
					</view>
				</view>

				<view class="uni-form-item uni-column">
					<view class="title">卡号码</view>
					<view class="content">
						<input class="uni-input" name="cardno" placeholder="必填" type="number" />
					</view>
				</view>

				<view class="uni-form-item uni-column">
					<view class="title">手机号</view>
					<view class="content">
						<input class="uni-input" name="phone" placeholder="必填" type="number" />
					</view>
				</view>
			</view>

			<view class="uni-form-item uni-column" style="padding: 20px 10px;border-bottom: none;">
				<view class="title" style="width: 120px;">设为默认就诊人</view>
				<view class="content" style="text-align: right;">
					<switch name="default" style="transform: scale(0.7,0.7)" />
				</view>
			</view>
			<view class="uni-btn-v">
				<button v-if="type == 'add'" type="primary" size="default" class="primarybtn" form-type="submit" @click="gotolast">添加就诊人</button>
				<view v-if="type == 'edit'" class="rowflex">
					<view style="width: 50%;">
						<button type="primary" size="default" class="regularbtn" style="width: 90%;">删除就诊人</button>
					</view>
					<view style="width: 50%;">
						<button type="primary" size="default" class="primarybtn" style="width: 90%;" form-type="submit" @click="gotolast">保存</button>
					</view>


				</view>
			</view>
		</form>
	</view>
</template>

<script>
	var graceChecker = require("../../../common/graceChecker.js");
	export default {
		data() {
			return {
				type: 'add', // add 为新增 edit 为修改
				id: '',
				relation: ['本人', '父母', '配偶', '子女', '其他'],
				array: ['就诊卡', '病历本'],
				form: {
					relation: 0,
					name: '',
					id: '',
					cardType: 0,
					cardNo: '',
					phone: '',
					default: '',
				},
			}
		},
		methods: {
			getUserInfo() {

			},
			formSubmit: function(e) {
				// console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))

				var formdata = e.detail.value
				// 姓名正则校验
				let reg_name = /^([\u4e00-\u9fa5]{2,20}|[a-zA-Z\.\s]{1,20})$/
				let sign_name = RegExp(reg_name).test(formdata.name);
				// 身份证正则校验
				let reg_idcard18 = /^[1-9]\d{5}(18|19|([23]\d))\d{2}((0[1-9])|(10|11|12))(([0-2][1-9])|10|20|30|31)\d{3}[0-9Xx]$/
				let reg_idcard15 = /^[1-9]\d{5}\d{2}((0[1-9])|(10|11|12))(([0-2][1-9])|10|20|30|31)\d{2}[0-9Xx]$/
				let sign_idcard18 = RegExp(reg_idcard18).test(formdata.idcard);
				let sign_idcard15 = RegExp(reg_idcard15).test(formdata.idcard);
				// 手机号正则校验
				let reg_phone = /^[1][3,4,5,7,8][0-9]{9}$/
				let sign_phone = RegExp(reg_phone).test(formdata.phone);
				if ((formdata.name).trim() == '') {
					this.showToast('请输入姓名');
				} else
				if (!sign_name) {
					this.showToast('姓名至少为2个字');
				} else
				if (!(sign_idcard18 || sign_idcard15)) {
					this.showToast('请检查证件号码是否正确');
				} else
				if ((formdata.cardno).trim() == '') {
					this.showToast('请输入卡号码');
				} else
				if ((formdata.phone).trim() == '') {
					this.showToast('请输入手机号');
				} else
				if (!sign_phone) {
					this.showToast('请检查手机号是否正确');
				} else {
					uni.showModal({
						title: '提示',
						content: '表单数据内容：' + JSON.stringify(formdata),
						showCancel: false
					});
				}
			},
			showToast(content) {
				uni.showToast({
					title: content,
					icon: "none"
					// content: content,
				})
			},
			//选择关系
			relationChange: function(e) {
				console.log('picker发送选择改变，携带值为', e.target.value)
				this.form.relation = e.target.value
				// this.arelation = this.relation[e.target.value]
			},
			//选择卡类型
			cardTypeChange: function(e) {
				console.log('picker发送选择改变，携带值为', e.target.value)
				this.form.cardType = e.target.value;
			},
			gotolast(){
				//判断从哪个页面进入，点击后返回该页面
				 var pages = getCurrentPages();
				 var prevPage = pages[pages.length - 2]; //上一个页面
				 // prevPage.$vm.sh = formdata.idcard,
				 uni.navigateBack({//返回
				 delta: 1
				 })
			}
		},
		onLoad: function(params) {
			this.type = params.params;
			this.id = params.id;
			console.log(this.type);
			// console.log(this.id);
		}
	}
</script>

<style scoped>
	.uni-form-item .title {
		/* padding: 10px 0; */
		width: 80px;
		font-size: 14px;
	}

	.uni-form-item {
		/* background-color: #FFFFFF; */
		border-bottom: #cccccc 1px solid;
		padding-bottom: 4px;
		display: flex;
		flex-wrap: nowrap;
		flex-direction: row;
		/* justify-content: center; */
		align-items: center;
		padding: 10px;
	}

	.uni-form-item .content {
		width: calc(100% - 80px);
		position: relative;
	}

	.arrowdown {
		position: absolute;
		right: 0px;
		top: 2px;
	}

	.uni-input {
		font-size: 14px;
	}
</style>
