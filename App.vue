<script>
export default {
	onLaunch: function() {
		console.log('App Launch');
	},
	onShow: function() {
		console.log('App Show');
	},
	onHide: function() {
		console.log('App Hide');
	}
};
</script>

<style>
/* 引入iconfont */
@import url("/static/iconfont/iconfont.css");
@import './static/css/index.css';
/* 给整个页面加上背景色，突出tarBar */
page {
	background-color: #f7f7f7;
	font-size: 20rpx;
	color: #000000;
	/* height: 100%; */
}
/* 解决头条小程序组件内引入字体不生效的问题 */
/* #ifdef MP-TOUTIAO */
@font-face {
	font-family: uniicons;
	src: url('/static/uni.ttf');
}
/* #endif */
</style>
