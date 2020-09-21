<template>
	<view class="fullscreen">
		<uni-search-bar placeholder="搜索科室" clearButton="auto" cancelButton="auto" radius="100" v-model="search" @input="input"></uni-search-bar>
		<view class="selectview">
			<view class="selectleft">
				<view class="keshi" v-for="(keshi, idx) in keshis" :key="idx" @click="choosekeshi(idx)" :class="{ keshiselected: idx == current }">
					<text class="keshisp ">{{ keshi.keshi }}</text>
				</view>
			</view>
			<view class="selectright">
				<view class="tip" v-for="(tip, j) in tips" :key="j" @click="choosetip(tip.tip)">
					<text class="keshisp ">{{ tip.tip }}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			current: '0',
			search: 'aaaa',
			tips: '',
			keshis: [
				{
					keshi: '推荐科室',
					tips: [{ tip: '测试科' }]
				},
				{
					keshi: '内科',
					tips: [
						{ tip: '呼吸科' },
						{ tip: '康复医学科' },
						{ tip: '泌尿科' },
						{ tip: '内分泌科' },
						{ tip: '妇产科' },
						{ tip: '皮肤科' },
						{ tip: '神经外科' },
						{ tip: '神经内科' },
						{ tip: '消化科' },
						{ tip: '心内科' },
						{ tip: '血液科' }
					]
				},
				{
					keshi: '外科',
					tips: [{ tip: '测试科' }]
				},
				{
					keshi: '皮肤性病科',
					tips: [{ tip: '测试科' }]
				},
				{
					keshi: '眼科',
					tips: [{ tip: '测试科' }]
				},
				{
					keshi: '耳鼻喉科',
					tips: [{ tip: '测试科' }]
				},
				{
					keshi: '口腔科',
					tips: [{ tip: '测试科' }]
				},
				{
					keshi: '肿瘤科',
					tips: [{ tip: '测试科' }]
				}
			]
		};
	},
	methods: {
		input() {
			console.log(this.search);
		},
		choosekeshi(idx) {
			var v = this;
			v.tips = v.keshis[idx].tips;
			v.current = idx;
		},
		choosetip(tip) {
			console.log(tip);
			uni.navigateTo({
				url: '../views/orderRegister2?params=' + tip
			});
		}
	},
	onLoad() {
		this.tips = this.keshis[0].tips;
	}
};
</script>

<style scoped>
page {
	height: 100%;
}
.selectview {
	height: calc(100% - 52px);
	display: flex;
	flex-direction: row;
	flex-wrap: nowrap;
}
.selectleft {
	height: 100%;
	overflow: auto;
	background-color: #e4e4e4;
	width: 50%;
	/* border-top: #d5d6d7 1px solid; */
	/* border-left: #d5d6d7 1px solid; */
}
.selectright {
	height: 100%;
	overflow: auto;
	background-color: #ffffff;
	width: 50%;
}
.keshi {
	padding: 10px 10px 10px 20px;
	border-bottom: #d5d6d7 1px solid;
	width: 100%;
}
.keshiselected {
	background-color: #ffffff;
}
.keshisp {
	font-family: 'Arial Normal', Arial, sans-serif;
	font-weight: 400;
	font-style: normal;
	font-size: 15px;
	color: #666666;
}
.tip {
	padding: 10px 10px 10px 20px;
	width: 100%;
}
</style>
