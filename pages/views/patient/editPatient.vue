<template>
	<view>
		<input v-model="form.phone" />
		<button @click="test">test</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				type: '', // add 为新增 edit 为修改
				id: '',
				relation: ['本人', '父母', '配偶', '子女', '其他'],
				form:{
					relation:'',
					name:'',
					id:'',
					cardType:'',
					cardNo:'',
					phone:''
				}
			}
		},
		methods: {
			getUserInfo() {

			},
			test(){
				console.log(this.form.phone);
			}
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
.uni-form-item{
	background-color: #FFFFFF;
	border-bottom: #000000 1px solid;
	padding-bottom: 4px;
}
</style>
