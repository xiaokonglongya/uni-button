<template>
	<view class="content">
		<view class="title margin-top">普通样式</view>
		<view class="margin-top box">
			<CcButton @cctap="showloading('isloading')" :loading="isloading">登陆</CcButton>
		</view>
		<view class="margin-top">
			<CcButton @cctap="showloading('isloading2')" fontsize="36rpx" height="120rpx" width="350rpx" color="#fff" bgcolor="rgba(252, 28, 143, 1)"
			 :loading="isloading2">支持自定义大小</CcButton>
		</view>
		<view class="margin-top">
			<CcButton @cctap="showloading('isloading3')" width="600rpx" color="#fff" bgcolor=" linear-gradient(-45deg, rgba(87, 225, 181, 1) 0%, rgba(0, 63, 255, 1) 100%);"
			 :loading="isloading3">渐变色按钮</CcButton>
		</view>
		<view class="title">加载中...</view>
		<view class="margin-top box">
			<CcButton @cctap="showloading('isloading')" :loading="true">加载中...</CcButton>
		</view>
		<view class="margin-top margin-top">
			<CcButton @cctap="showloading('isloading2')" fontsize="36rpx" height="120rpx" width="350rpx" color="#fff" bgcolor="rgba(252, 28, 143, 1)"
			 :loading="true">支持自定义大小</CcButton>
		</view>
		<view class="margin-top">
			<CcButton @cctap="showloading('isloading3')" width="600rpx" color="#fff" bgcolor=" linear-gradient(-45deg, rgba(87, 225, 181, 1) 0%, rgba(0, 63, 255, 1) 100%);"
			 :loading="true">渐变色按钮</CcButton>
		</view>
		<view class="title">禁用</view>
		<view class="margin-top box">
			<CcButton @cctap="showloading('isloading')" :isdisable="true" >禁用</CcButton>
		</view>
		<view class="margin-top margin-top">
			<CcButton @cctap="showloading('isloading2')" :isdisable="true" :loading="true" fontsize="36rpx" height="120rpx" width="350rpx" color="#fff" bgcolor="rgba(252, 28, 143, 1)"
			 >禁用</CcButton>
		</view>
		<view class="margin-top">
			<CcButton @cctap="showloading('isloading3')" :isdisable="true" width="600rpx" color="#fff" bgcolor=" linear-gradient(-45deg, rgba(87, 225, 181, 1) 0%, rgba(0, 63, 255, 1) 100%);"
			 >禁用</CcButton>
		</view>
	</view>
</template>

<script>
	import CcButton from '@/components/cc-button/cc-button.vue';
	export default {
		data() {
			return {
				title: 'Hello',
				isloading: false,
				isloading2: false,
				isloading3: false
			};
		},
		components: {
			CcButton
		},
		onLoad() {},
		methods: {
			showloading(type) {
				this[type] = true
				setTimeout(() => {
					this[type] = false
				}, 3500);
			}
		}
	};
</script>

<style>
	.title{
		text-align: center;
		font-size: 28rpx ;
		font-weight: 700;
	}
	.margin-top {
		margin-top: 10rpx;
	}
</style>
