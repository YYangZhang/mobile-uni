<template>
	<view>
		<form @submit="formSubmit" @reset="formReset">

			<view style="padding: 0 10px;background-color: #FFFFFF;">

				<view class="uni-form-item uni-column">
					<view class="title">关系</view>
					<picker @change="bindPickerChange" :value="index" name="relation" :range="relation" style="border: red 1px solid;">
						<view class="uni-input">{{relation[index]}}</view>
					</picker>
				</view>
				<view class="uni-list-cell">
					<view class="uni-list-cell-left">
						当前选择
					</view>
					<view class="uni-list-cell-db" style="border: red 1px solid;">
						<picker @change="bindPickerChange" :value="index" :range="array" style="border: red 1px solid;">
							<view class="uni-input">{{array[index]}}</view>
						</picker>
					</view>
				</view>
				
				<view class="uni-form-item uni-column">
					<view class="title">姓名</view>
					<input class="uni-input" name="name" placeholder="必填" />
				</view>

				<view class="uni-form-item uni-column">
					<view class="title">身份证号</view>
					<input class="uni-input" name="idcard" placeholder="必填" />
				</view>

				<view class="uni-form-item uni-column">
					<view class="title">卡类型</view>
					<input class="uni-input" name="name" placeholder="必填" />
				</view>

				<view class="uni-form-item uni-column">
					<view class="title">卡号码</view>
					<input class="uni-input" name="cardno" placeholder="必填" />
				</view>

				<view class="uni-form-item uni-column">
					<view class="title">手机号</view>
					<input class="uni-input" name="phone" placeholder="必填" />
				</view>

				<view class="uni-form-item uni-column">
					<view class="title" style="width: 120px;">设为默认就诊人</view>
					<view class="content">
						<switch name="switch" />
					</view>
				</view>

			</view>
			<view class="uni-btn-v">
				<button form-type="submit">Submit</button>
				<button type="default" form-type="reset">Reset</button>
			</view>
		</form>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				type: '', // add 为新增 edit 为修改
				id: '',
				relation: ['本人', '父母', '配偶', '子女', '其他'],
				array: ['中国', '美国', '巴西', '日本'],
				form: {
					relation: '',
					name: '',
					id: '',
					cardType: '',
					cardNo: '',
					phone: ''
				}
			}
		},
		methods: {
			getUserInfo() {

			},
			formSubmit: function(e) {
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
				var formdata = e.detail.value
				uni.showModal({
					content: '表单数据内容：' + JSON.stringify(formdata),
					showCancel: false
				});
			},
			formReset: function(e) {
				console.log('清空数据')
			},
			bindPickerChange: function(e) {
				console.log('picker发送选择改变，携带值为', e.target.value)
				this.index = e.target.value
			},
		},
		onLoad: function(params) {
			this.type = params.params;
			this.id = params.id;
			console.log(this.type);
			console.log(this.id);
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
		background-color: #FFFFFF;
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
		width: calc(100% - 60px);
		text-align: right;
		font-size: 10px;
	}

	.uni-input {
		font-size: 14px;
	}
</style>
