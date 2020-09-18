<template>
	<view>
		<view style="text-align: center;padding-top: 250rpx;">
			<text class="iconfont iconorder"></text>
			<view class="div">
				<text class="test">The More Page</text>
				<view style="height: 20px;"></view>
				<text  class="test">{{params}}</text>
			</view>
			
		</view>
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
		}
	}
</script>

<style scoped>

page{
	background-color: #FFFFFF;
}
.iconorder{
	font-size: 4rem;
	color: #DD524D;
}
.div{
	/* width: 300rpx; */
	margin: 0 auto;
	text-align: center;
	padding-top: 40rpx;
}
.test{
	font-size: 50rpx;
}
</style>
