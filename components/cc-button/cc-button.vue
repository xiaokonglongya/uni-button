<template>
  <view class="button-container">
    <button
      hover-class="none"
      @tap="tap"
      @click="onclick"
      :disabled="isdisable"
      :style="{
		opacity: isdisable?'0.8':'1',
		color:color,
		background:bgcolor,
		width:(loading&&!isdisable?height:width),
		height:height,
		lineHeight:height,
		fontSize:fontsize,
		borderRadius: height
		}"
      :class="['button',((loading&&!isdisable) ? 'loading' : '')]"
    >
      <view v-if="!loading||isdisable" class="content">
        <slot></slot>
      </view>
      <view
        v-if="loading&&!isdisable"
        class="loader-03"
        :style="{
				width:loadingsize,
				height:loadingsize,
				borderWidth:borderWidth
			}"
      ></view>
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
    color: {
      type: String,
      default: "#ffffff"
    },
    bgcolor: {
      type: String,
      default: "#333333"
    },
    width: {
      type: String,
      default: "200rpx"
    },
    height: {
      type: String,
      default: "100rpx"
    },
    borderWidth: {
      type: String,
      default: "3rpx"
    },
    fontsize: {
      type: String,
      default: "25rpx"
    },
    isdisable: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    tap() {
      this.$emit("cctap");
    },
    onclick() {
      this.$emit("cclick");
    }
  },
  computed: {
    loadingsize: function() {
      const str = this.height;
      if (str.indexOf("rpx") != -1) {
        return str.slice(0, str.indexOf("rpx")) / 4 + "rpx";
      } else if (str.indexOf("upx") != -1) {
        return str.slice(0, str.indexOf("upx")) / 4 + "upx";
      } else {
        return "25rpx";
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.button-container {
  margin: 0 30rpx;
  display: flex;

  .button {
    padding: 0px;
    transition: 0.35s ease all;
    // 开启3D加速
    transform: translate3d(0rpx, 0rpx, 0rpx);
    display: flex;
    justify-content: center;
    align-items: center;

    &:before {
      display: none;
    }

    &:after {
      display: none;
    }
  }
  .button.loading {
    font-weight: 100;
  }

  .button.loading .content {
    position: absolute;
  }

  .button.loading .loader-03 {
    position: absolute;
  }

  .button.disabled {
    pointer-events: none;
  }

  .loader-03 {
    color: inherit;
    vertical-align: middle;
    pointer-events: none;
    border-style: solid;
    border-color: currentcolor;
    border-bottom-color: transparent;
    border-radius: 50%;
    animation: 2s loader-03 linear infinite;
    position: absolute;
  }
}

@keyframes loader-03 {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}
</style>
