<template>
	<view class="content">
		<view class="main clear">
			<!-- --------首页导航--------------------------------------- -->
			<view class="header flex_between">
				<view>
					<view class="site" v-show="site">
						{{ site }}
						<text class="icon"></text>
					</view>
				</view>
				<view>
					<view class="flex_between nav_title">
						<text v-for="(item, i) of navs" :key="i" :class="{ select: isActive == i }" @click="onSelect(i)">{{ item }}</text>
					</view>
				</view>
				<view><text class="iconfont">&#xe8ee;</text></view>
			</view>
			<!-- --------热映标签你页-------------------------------------- -->
			<view v-show="isActive === 0" class="main_renying main_1">
				<!-- 为空显示这个 -->
				<view class="empty" v-if="re_status === 1">
					<view>
						<text class="iconfont">&#xe699;</text>
						<view class="text">暂无热映电影</view>
					</view>
				</view>
				<!-- 未定位显示这个 -->
				<view class="empty" v-if="re_status === 2">
					<view>
						<text class="iconfont">&#xe6a8;</text>
						<view class="text">自动定位失败，请手动选择城市</view>
						<button type="default" size="mini">选择城市</button>
					</view>
				</view>
				<view class="main_reying_content"></view>
			</view>
			<!-- --------待映标签页-------------------------------------- -->
			<view v-show="isActive === 1" class="main_daiying main_1">
				<view class="top_popular">
					<view class="top_popular_title"><text>近期最受欢迎</text></view>
					<!-- 横向滑块 -->
					<view class="scroll-view">
						<!-- 推荐电影区 结构样式 -->
						<view v-for="(item,i) in scroll_movies" :key="item">
							<view class="movie_img">
								<view class="icon_xin">
									<text class="iconfont">&#xe8ab;</text>
								</view>
								<image src="https://bk.bklei.com/img/0.jpg" mode=""></image>
							</view>
							<view class="movie_text">
								<view class="title">
									<text>海贼王之桃之助必须死</text>
								</view>
								<view class="">
									<text>64亿人想看</text>
								</view>
								<view class="">
									<text>5月1日</text>
								</view>
							</view>
						</view>
					</view>
				</view>
				<view class="movie_list">
					<view class="movie" v-for="(item,index) in movie_list" :key="item">
						<view class="movie_date">
							<text>4月30日 周四</text>
						</view>
						<view class="flex_between">
							<view class="movie_img">
								<image src="https://bk.bklei.com/img/0.jpg" mode=""></image>
							</view>
							<view class="movie_text">
								<view class="title">大红包</view>
								<view class="">喜剧，爱奇</view>
								<view class="">主演：包贝尔,克拉拉,贾冰</view>
								<view class="">2020-04-30大陆上映</view>
							</view>
							<view class="movie_btn">
								<view class="total">
								   <text>515454</text>
								   <text style="font-size:18rpx">人想看</text>
								</view>
								<view class="btn">
									<button type="default" size="mini"><text class="iconfont">&#xe8ab;</text>想看</button>
									
								</view>
							</view>
						</view>
						
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			site: '郑州', //当前城市
			navs: ['热映', '待映'],
			isActive: 1, //标签页切换 默认0热映
			re_status: 1, //热映标签页状态 0代表无状态 1代表无数据  2代表没有定位and没有获取地址  通过接口请求的数据和用户操作再判断状态
			scroll_movies:[1,2,3,4,5,6,7,8,9,10,11,12,13],
			movie_list:[1,2,3,4,5,6,7]
		};
	},
	onLoad() {},
	methods: {
		onSelect(i) {
			this.isActive = i; //改变isActive切换标签页
		}
	}
};
</script>

<style lang="scss">
.content {
	width: 100%;
	height: 100%;
	position: absolute;
	top: 0px;
	bottom: 0px;
}
.header {
	height: 70rpx;
	padding: 0rpx 20rpx;
	border-bottom: 0.5px solid #f5f5f5;
	background-color: $uni-bg-color;
	view {
		.iconfont {
			color: $uni-text-color-red;
			font-size: $uni-font-size-lg;
		}
		.site {
			font-size: $uni-font-size-base;
			color: $uni-text-color-grey;
			.icon {
				border-top: 10rpx solid $uni-text-color-grey;
				border-left: 10rpx solid transparent;
				border-right: 10rpx solid transparent;
				border-bottom: 10rpx solid transparent;
				position: relative;
				top: 18rpx;
				left: 6rpx;
			}
		}
	}
}
.nav_title {
	height: 70rpx;
	text {
		height: 70rpx;
		padding: 0 15rpx;
		margin: 0 20rpx;
		font: bold;
		line-height: 70rpx;
		box-sizing: border-box;
	}
	.select {
		color: $uni-text-color-red;
		border-bottom: 4rpx solid $uni-text-color-red;
	}
}
.main {
	height: 100%;
	background-color: $uni-bg-color-grey;
	// 热映 待映标签页 通用设置
	.main_1 {
		// height: 100%;
		width: 100%;
		float: left;
		// padding: 20rpx 20rpx 0;
		box-sizing: border-box;
	}
	// 热映标签页样式
	.main_renying {
		.empty {
			height: 70vh;
			display: flex;
			align-items: center;
			justify-content: center;
			view {
				text-align: center;
				text {
					font-size: 200rpx;
					color: $uni-text-color-red;
				}
				.text {
					margin: 20rpx 0;
				}
				button {
					color: $uni-text-color-red;
					border: 1px solid $uni-text-color-red;
				}
			}
		}
	}
	// 待映标签页样式
	.main_daiying {
		height: 75%;
		.top_popular{
			padding: 20rpx 20rpx;
			margin-bottom: 20rpx;
			background-color: $uni-bg-color;
			.top_popular_title{
				padding-bottom:20rpx;
				font-size: $uni-font-size-sm;
			}
			.scroll-view{
				display: flex;
				flex-wrap: nowrap;
				overflow-x: auto;
				padding-bottom:20rpx;
				view{
					width: 200rpx;
					margin-right:20rpx;
					.movie_img{
						width: 200rpx;
						// height: 234rpx;
						height: 290rpx;
						overflow: hidden;
						position: relative;
						.icon_xin{
							width: 50rpx;
							height: 50rpx;
							text-align: center;
							line-height: 50rpx;
							background-color:rgba(0,0,0,0.3);
							position: absolute;
							left:0;
							top:0;
							z-index: 999;
							.iconfont{
								color:red;
								font-size: 30rpx;
							}
						}
						image{
							width: 100%;
							height: 100%;
						}
					}
					.movie_text{
						color: $uni-text-color-grey;
						font-size: $uni-font-size-sm;
						view{
							margin-top:2rpx;
						}
						.title{
							width: 150rpx;
							color:$uni-text-color-hei;
							overflow: hidden;
							text-overflow:ellipsis;
							white-space: nowrap;
						}
					}
				}
			}
		}
		
		.movie_list{
			padding: 0 20rpx;
			background-color: $uni-bg-color;
			height: 70%;
			.movie{
				padding-bottom: 20rpx;
				border-bottom:1rpx solid #f5f5f5;
				view{
					margin-bottom:5rpx;
				}
				.movie_date{
					padding: 20rpx 0;
					font-size:$uni-font-size-sm;
					color:#555555;
				}
				.movie_img{
					image{
						width: 170rpx;
						height: 220rpx;
					}
				}
				.movie_text{
					width: 51%;
					color:#808080;
					font-size:$uni-font-size-sm;
					.title{
						color:$uni-text-color-hei;
						font-size: $uni-font-size-lg;
					}
				}
				.movie_btn{
					view{
						margin: 20rpx 0;
						float: right;
					}
					.total{
						color:$uni-text-color-huang;
					}
					.btn{
						position: relative;
						button{
							height: 60rpx;
							line-height: 60rpx;
							font-size:20rpx;
							border:1px solid $uni-text-color-red;
							color:$uni-text-color-red;
							.iconfont{
								margin-right:5rpx ;
							}
						}
					
					}
				}
			}
		}
	}
}
</style>
