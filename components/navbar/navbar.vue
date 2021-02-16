<template>
	<view class="navbar">
		<view class="navbar-container" :style="{ height: fullHeight + 'rpx' }"></view>
		<view class="navbar-content">
			<view class="navbar-status" :style="{ height: statusBarHeight + 'rpx' }"></view>
			<view 
			  class="navbar-header" 
				:style="{ height: navBarHeight + 'rpx', width: navBarContentWidth + 'rpx' }"
			>
				<view class="navbar-search">
					<view class="navbar-search-icon">
						<uni-icons type="search" size="16" color="#999"></uni-icons>
					</view>
					<view class="navbar-search-text">
						uni-app
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'Navbar',
		data() {
			return {
				statusBarHeight: 0,
				navBarHeight: 88,
				navBarContentWidth: 750
			};
		},
		computed: {
			fullHeight() {
				return this.statusBarHeight + this.navBarHeight;
			}
		},
		mounted () {
		  this.initHeight();
		},
		methods: {
			initHeight () {
				const systemInfo = uni.getSystemInfoSync();
				this.statusBarHeight = systemInfo.statusBarHeight * 2;
				// this.navBarContentWidth = systemInfo.windowWidth * 2;
				
				// #ifndef H5 || APP-PLUS || MP-ALIPAY
				const menuInfo =  uni.getMenuButtonBoundingClientRect();
				this.navBarHeight = ((menuInfo.bottom + menuInfo.top) - this.statusBarHeight) * 2;
				this.navBarContentWidth = menuInfo.left * 2;
				// #endif
			}
		}
	}
</script>

<style lang="scss">
	.navbar-content {
		position: fixed;
		top: 0;
		right: 0;
		left: 0;
		background-color: $news-base-color;

		.navbar-header {
			display: flex;
			align-items: center;
			padding: 0 30rpx;
			box-sizing: border-box;

			.navbar-search {
				width: 100%;
				height: 60rpx;
				line-height: 60rpx;
				background-color: #fff;
				border-radius: 60rpx;
				padding: 0 20rpx;
				
				.navbar-search-icon {
					display: inline-block;
				}
				
				.navbar-search-text {
					display: inline-block;
					color: #999;
					font-size: 28rpx;
					text-indent: 10rpx;
					vertical-align: bottom;
				}
			}
		}

	}
</style>
