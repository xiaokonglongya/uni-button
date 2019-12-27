<template>
	<view class="button-container">
		<button hover-class="none"  :disabled="loading" :style="{
		color:color,
		backgroundColor:bgcolor,
		width:(loading?height:width),
		height:height	
		}"
		:class="['button',(loading ? 'loading' : '')]">
			<view class="content"><slot></slot></view>
			<view class="loader-03" :style="{
				borderWidth:borderWidth
			}"></view>
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
		},
		color:{
			type:String,
			default:'#ffffff'
		},
		bgcolor:{
			type:String,
			default:'#333333'
		},
		width:{
			type:String,
			default:'200rpx'
		},
		height:{
			type:String,
			default:'80rpx'
		},
		borderWidth:{
			type:String,
			default:'3rpx'
		}
	}
};
</script>

<style lang="scss" scoped>
.button-container {
	margin: 0 30rpx;
	display: flex;
	.button {
		font-weight: 100;
		padding: 0px;
		border-radius: 50rpx;
		font-size: 30rpx;
		transition: 0.25s ease all;
		display: flex;
		justify-content: center;
		align-items: center;
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
		border-style:solid;
		border-color: currentcolor;
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
