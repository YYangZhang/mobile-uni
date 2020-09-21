<template>
	<view>
		{{params}}
	</view>
</template>

<script>
	export default {
		data() {
			return {
				params:''
			}
		},
		methods: {
			
		},
		onLoad:function(params){
			this.params = params.params;
			console.log(this.params)
		}
	}
</script>

<style scoped>

</style>
