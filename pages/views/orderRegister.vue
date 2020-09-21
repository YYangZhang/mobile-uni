<template>
	<view class="fullscreen">
		<uni-search-bar placeholder="搜索科室" clearButton="auto" cancelButton="auto" radius="100" v-model="search"
		 @input="input"></uni-search-bar>
		 <view class="selectview">
		 	<view class="selectleft">
				<view class="keshi keshiselected">
					<text class="keshisp ">内科</text>
				</view>
			</view>
			<view class="selectright">
				
			</view>
		 </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				search: "aaaa"
			}
		},
		methods: {
			input() {
				console.log(this.search)
			}
		}
	}
</script>

<style scoped>
	page {
		height: 100%;
	}
	.selectview{
		height: calc(100% - 52px);
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
	}
	.selectleft{
		height: 100%;
		overflow: auto;
		background-color: #e4e4e4;
		width: 50%;
		/* border-top: #d5d6d7 1px solid; */
		/* border-left: #d5d6d7 1px solid; */
	}
	.selectright{
		height: 100%;
		overflow: auto;
		background-color: #FFFFFF;
		width: 50%;
	}
	.keshi{
		padding: 10px 10px 10px 20px;
		border-bottom: #d5d6d7 1px solid;
		width: 100%;
	}
	.keshiselected{
		background-color: #FFFFFF;
	}
	.keshisp{
		font-family: "Arial Normal", Arial, sans-serif;
		    font-weight: 400;
		    font-style: normal;
			font-size: 15px;
			color: #666666;
	}
</style>
