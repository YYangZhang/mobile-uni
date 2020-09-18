<template>
	<view style="border: red 1px solid;height: 100%;" @click="test">
		service
		
		test github2
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			test(){
				uni.navigateTo({
					url:"../info/test"
				})
			}
		}
	}
</script>

<style scoped>

</style>
