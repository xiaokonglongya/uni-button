<template>
	<view class="button-container">
		<button hover-class="none"  :disabled="loading" :class="'button ' + (loading ? 'loading' : '')">
			<view class="content"><slot></slot></view>
			<view class="loader-03"></view>
		</button>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	props: {
		loading: {
			type: Boolean,
			default: false
		}
	}
};
</script>

<style lang="scss" scoped>
.button-container {
	margin: 0 30rpx;
	display: flex;
	.button {
		background: #666 !important;
		color: #fff !important;
		font-weight: 100;
		padding: 0px;
		height: 90rpx !important;
		width: 100% !important;
		min-width: 100rpx;
		border-radius: 50rpx;
		font-size: 30rpx;
		transition: 0.25s ease all;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.button.loading {
		width: 90rpx !important;
	}
	.button.loading .content {
		display: none;
	}
	.button.loading .loader-03 {
		display: block;
	}

	.button.disabled {
		pointer-events: none;
	}

	.loader-03 {
		width: 35rpx;
		height: 35rpx;
		color: inherit;
		vertical-align: middle;
		pointer-events: none;
		border: 3rpx solid currentcolor;
		border-bottom-color: transparent;
		border-radius: 50%;
		animation: 2s loader-03 linear infinite;
		position: relative;
		display: none;
	}
}

@keyframes loader-03 {
	0% {
		-webkit-transform: rotate(0deg);
		transform: rotate(0deg);
	}
	100% {
		-webkit-transform: rotate(360deg);
		transform: rotate(360deg);
	}
}
</style>
