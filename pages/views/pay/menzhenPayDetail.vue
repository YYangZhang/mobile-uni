<template>
	<view>
		<view class="div1 blue">
			费用明细
			<view style="padding-top: 16px;">
				<image src="../../../static/img/txm.jpg" style="width: 100%;height: 80px;"></image>
			</view>

		</view>
		<view style="height: 10px;background-color: #f7f7f7;"></view>
		<view style="padding: 0 10px;">
			<view class="div2 flex">
				<view class="div3 txtleft blue">
					项目名称
				</view>
				<view class="div3 txtcenter blue">
					数量
				</view>
				<view class="div3 txtright blue">
					金额
				</view>
			</view>

			<view class="div2 flex" v-for="(list,index) in lists" :key="index">
				<view class="div3 txtleft ">
					<view class="sp1">
						{{list.name}}
					</view>
					<view class="sp2" style="padding-top: 4px;">
						￥{{list.price}}
					</view>
				</view>
				<view class="div3 txtcenter sp2">
					{{list.nums}}
				</view>
				<view class="div3 txtright sp1">
					￥{{list.total}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				lists: [{
						name: '金嗓子',
						price: '20',
						nums: '2',
						total: '40',
					},
					{
						name: '纱布',
						price: '50',
						nums: '1',
						total: '50',
					},
					{
						name: '999感冒灵',
						price: '100',
						nums: '2',
						total: '200',
					}
				]
			}
		},
		methods: {

		}
	}
</script>

<style scoped>
	page {
		background-color: #FFFFFF;
	}

	.div1 {
		padding: 10px;
		background-color: #FFFFFF;
		text-align: center;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-size: 14px;
	}

	.div2 {
		padding: 10px 0;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-size: 13px;
		flex-direction: row;
		flex-wrap: nowrap;
		align-items: flex-end;
		border-bottom: #e8e8e8 1px solid;


	}

	.div3 {
		width: 33%;
	}

	.sp1 {
		font-size: 14px !important;
		color: #434343;
	}

	.sp2 {
		font-size: 13px !important;
		color: #9a9a9a;
	}
</style>
