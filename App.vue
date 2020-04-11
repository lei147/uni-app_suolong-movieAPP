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
@font-face {
	font-family: 'iconfont'; /* project id 1748477 */
	src: url('//at.alicdn.com/t/font_1748477_9v3i48ckbgk.eot');
	src: url('//at.alicdn.com/t/font_1748477_9v3i48ckbgk.eot?#iefix') format('embedded-opentype'), url('//at.alicdn.com/t/font_1748477_9v3i48ckbgk.woff2') format('woff2'),
		url('//at.alicdn.com/t/font_1748477_9v3i48ckbgk.woff') format('woff'), url('//at.alicdn.com/t/font_1748477_9v3i48ckbgk.ttf') format('truetype'),
		url('//at.alicdn.com/t/font_1748477_9v3i48ckbgk.svg#iconfont') format('svg');
}
.iconfont {
	font-family: 'iconfont' !important;
	font-size: 16px;
	font-style: normal;
	-webkit-font-smoothing: antialiased;
	-webkit-text-stroke-width: 0.2px;
	-moz-osx-font-smoothing: grayscale;
}
/*每个页面公共css */
.flex_between {
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.clear {
	clear: both;
	content: '';
	display: block;
	height: 0;
}
</style>
