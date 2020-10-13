<template>
	<view>
		<view class="detailtop">
			<text class="name">血常规</text>
			<view class="rptDdiv2">
				<view class="flex rptDdiv1">
					<view class="rptDsp1">姓名：</view>
					<view class="rptDsp2">张耀扬</view>
					<view class="rptDsp3">性别：</view>
					<view class="rptDsp4">男</view>
				</view>
				<view class="flex rptDdiv1">
					<view class="rptDsp1">年龄：</view>
					<view class="rptDsp2">18</view>
					<view class="rptDsp3">送检日期：</view>
					<view class="rptDsp4">2020-07-22</view>
				</view>
			</view>
		</view>
		<view class="detailbot">
			<view class="bluediv" v-if="reportType == '1' || reportType == '2' || reportType == '3'">
				报告结果
				<view class="download">
					<text class="iconfont iconxiazai"></text>
					下载
				</view>
			</view>

			<view class="reportall" v-if="reportType == '1'">
				<view class="flex rptDdiv3 borderbottom color666">
					<view class="rptDdiv4">
						项目：
					</view>
					<view class="rptDdiv4 blue txtcenter">
						ABO血型
					</view>
					<view class="rptDdiv4 blue txtcenter">
						RH血型
					</view>
				</view>

				<view class="flex rptDdiv3 color666">
					<view class="rptDdiv4">
						检查结果：
					</view>
					<view class="rptDdiv4 orange txtcenter">
						A
					</view>
					<view class="rptDdiv4 orange txtcenter">
						+
					</view>
				</view>
			</view>

			<view class="reportall" v-if="reportType == '2'">
				<view class="reportConcu blue">
					检查结论
				</view>
				<view class="reportDetail color999">
					中性杆状核粒细胞增高见于急性化脓性感染、 大出血、严重组织损伤、慢性粒细胞膜性白血病及安眠药中毒等。 中性分叶核粒细胞减少多见于某些传染病、再生障碍性贫血、粒细胞缺乏症等。
					嗜酸性粒细胞增多见于牛皮癣、天疤疮、湿疹、支气管哮喘、食物过敏，一些血液病及肿瘤，如慢性粒细胞性白血病、鼻咽癌、肺癌以及宫颈癌等。
				</view>
				<view class="reportConcu blue">
					检查详情
				</view>
				<view class="reportDetail color999">
					嗜酸性粒细胞减少见于伤寒、副伤寒早期、长期使用肾上腺皮质激素后。 淋巴细胞增高见于传染性淋巴细胞增多症、结核病、疟疾、慢性淋巴细胞白血病、百日咳、某些病毒感染等。 淋巴细胞减少见于淋巴细胞破坏。
				</view>
			</view>

			<view class="reportall" v-if="reportType == '3'">
				<view class="flex rptDdiv3 borderbottom color666">
					<view class="rptDdiv4 txtcenter">
						项目
					</view>
					<view class="rptDdiv4  txtcenter">
						检查结果
					</view>
					<view class="rptDdiv4  txtcenter">
						参考值
					</view>
				</view>

				<view class="flex rptDdiv3 color666 borderbottom">
					<view class="rptDdiv4 warnred txtcenter">
						细菌计数
					</view>
					<view class="rptDdiv4 warnred txtcenter">
						28.5
					</view>
					<view class="rptDdiv4 warnred txtcenter">
						0.0~26.4/UL
					</view>
				</view>

				<view class="flex rptDdiv3 color333">
					<view class="rptDdiv4 txtcenter">
						酵母菌
					</view>
					<view class="rptDdiv4 txtcenter">
						阴性
					</view>
					<view class="rptDdiv4 txtcenter">
						阴性
					</view>
				</view>
			</view>

			<view class="report1 color999"  v-if="reportType == '4'">
				点击后可缩放查看
				<view class="img-wrap">
					<image src="../../../static/img/1.jpg" @click="TanPreviewImage('../../../static/img/1.jpg')"></image>
				</view>
			</view>
		</view>


		<view style="padding: 0 10px 20px;font-size: 14px;color: #999999;">
			<uni-icons type="info" size="15" color="#258efc" style="margin-right: 4px;"></uni-icons>
			<text>
				此报告仅作参考，以医院实际纸质报告为准。
			</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				reportType: 4, //报告种类
			};
		},
		onLoad:function(params){
			this.reportType = params.params;
		},
		methods: {
			TanPreviewImage(imageUrl) {
				// 点击查看图片详情
				console.log(imageUrl)
				var images = [];
				images.push(imageUrl);
				console.log(images)
				uni.previewImage({ // 预览图片  图片路径必须是一个数组 => ["http://192.168.100.251:8970/6_1597822634094.png"]
					current: 0,
					urls: images,
					longPressActions: { //长按保存图片到相册
						itemList: ['保存图片'],
						success: (data) => {
							console.log(data);
							uni.saveImageToPhotosAlbum({ //保存图片到相册
								filePath: payUrl,
								success: function() {
									uni.showToast({
										icon: 'success',
										title: '保存成功'
									})
								},
								fail: (err) => {
									uni.showToast({
										icon: 'none',
										title: '保存失败，请重新尝试'
									})
								}
							});
						},
						fail: (err) => {
							console.log(err.errMsg);
						}
					}
				});
			},
		}
	};
</script>

<style scoped>
	.detailtop {
		background-color: #ffffff;
		padding: 18px 0 30px 0;
	}

	.name {
		padding: 2px 12px 3px 10px;
		background-color: #12bde8;
		color: #ffffff;
		width: auto;
		display: inline-block;
		border-radius: 0 11px 11px 0;
		font-family: 'Arial Normal', Arial, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 13px;
	}

	.rptDdiv2 {
		padding: 10px 20px 0 20px;
	}

	.rptDdiv1 {
		flex-direction: row;
		flex-wrap: nowrap;
		padding-top: 10px;
		align-items: center;
	}

	.rptDsp1 {
		width: 50px;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #333333;
	}

	.rptDsp2 {
		width: calc(45% - 50px);
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #666666;
	}

	.rptDsp3 {
		width: 80px;
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #333333;
	}

	.rptDsp4 {
		width: calc(55% - 80px);
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 14px;
		color: #666666;
	}

	.detailbot {
		padding: 10px;
	}

	.bluediv {
		height: 40px;
		position: relative;
		text-align: center;
		width: 100%;
		background-color: #258efc;
		border-radius: 4px 4px 0 0;
		line-height: 40px;
		font-family: 'Arial Negreta', 'Arial', sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 16px;
		color: #ffffff;
	}

	.download {
		position: absolute;
		color: #ffffff;
		right: 10px;
		top: 0;
	}

	.iconxiazai {
		font-size: 22px;
		font-weight: 400;
		line-height: normal;
		position: relative;
		top: 3px;
		margin-right: 4px;
	}

	.reportall {
		padding: 2px 10px;
		border: #e5e7eb 1px solid;
		background-color: #FFFFFF;
		border-radius: 0 0 4px 4px;
	}

	.rptDdiv3 {
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: space-between;
		align-items: center;
		padding: 14px 0;
		font-family: 微软雅黑, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 13px;
	}

	.rptDdiv4 {
		width: 33%;
	}

	.rptDdiv3:not(:last-child) {
		border-bottom: 1px solid #f5f5f5;
	}

	.reportConcu {
		padding-top: 20px;
		font-family: 'Arial Negreta', 'Arial', sans-serif;
		font-weight: 700;
		font-style: normal;
		font-size: 14px;
	}

	.reportDetail {
		padding: 10px;
		font-family: 微软雅黑, sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 13px;
		text-indent: 20px;
	}

	.report1 {
		font-family: 'Arial Normal', 'Arial', sans-serif;
		font-weight: 400;
		font-style: normal;
		font-size: 12px;
	}

	.img-wrap {
		width: 100%;
	}

	.img-wrap image {
		width: 100%;
		/* height: auto; */
	}
</style>
