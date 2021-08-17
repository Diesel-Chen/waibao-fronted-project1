<template>
  <view
    class="checkbox-list-body"
    v-show="visible"
  >

    <view class="wrap">

      <view class="head">
        <view
          class="left"
          :class="{'btn-on':checkedList.length === dataTop.length }"
          @click="handleAllSelct"
        >全选</view>
        <view
          class="right"
          @click="handleInvertSelect"
        >反选</view>
      </view>

      <view class="mid">
        <u-row gutter="20">
          <u-col
            span="4"
            v-for="item in dataTop"
            :key="item.id"
          >
            <view
              :class="{'on':checkedList.includes(item.id)}"
              class="col-item"
              @click="handleCol(item)"
            >{{item.label}}</view>
          </u-col>

        </u-row>
      </view>

      <view class="bottom">
        <view
          class="left"
          @click="cancel"
        >取消</view>
        <view
          class="right"
          @click="confirm"
        >确定</view>
      </view>
    </view>

  </view>
</template>

<script>
export default {
  props: {
    visible: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      checkedList: [],
      dataTop: [
        {
          id: 0,
          label: "混合过关",
        },
        {
          id: 1,
          label: "胜平负",
        },
        {
          id: 2,
          label: "让球胜平负",
        },
        {
          id: 3,
          label: "总进球",
        },
        {
          id: 4,
          label: "比分",
        },
        {
          id: 5,
          label: "半全场",
        },
      ],
    };
  },
  methods: {
    cancel() {
      this.$emit("update:visible", false);
    },
    confirm() {
      this.$emit("update:visible", false);
    },

    handleCol(item) {
      const index = this.checkedList.indexOf(item.id);
      if (index === -1) {
        this.checkedList.push(item.id);
        return;
      }
      this.checkedList.splice(index, 1);
    },

    handleAllSelct() {
      this.checkedList = this.dataTop.map((item) => item.id);
    },

    handleInvertSelect() {
      this.checkedList = this.dataTop
        .filter((item) => {
          return !this.checkedList.includes(item.id);
        })
        .map((item) => item.id);
    },
  },
};
</script>

<style lang="scss" scoped>
.checkbox-list-body {
  position: fixed;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  z-index: 9;
  background: rgba(#000000, 0.1);
  .wrap {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    padding: 0 20rpx;
    width: 90vw;
    background: #fff;
    .title {
      padding: 20rpx 10rpx;
    }
    .col-item {
      height: 80rpx;
      color: grey;
      border: 2rpx solid #f0f0f0;
      margin-bottom: 20rpx;
      line-height: 80rpx;
      text-align: center;
    }
    .head {
      display: flex;
      justify-content: space-around;
      padding: 30rpx 0;
      .left,
      .right {
        height: 70rpx;
        width: 230rpx;
        border: 2rpx solid #f0f0f0;
        line-height: 70rpx;
        text-align: center;
      }
    }
    .mid {
      border-top: 2rpx solid #f0f0f0;
      padding: 40rpx 0 30rpx 0;
    }
    .bottom {
      height: 100rpx;
      display: flex;
      border-top: 2rpx solid #f0f0f0;
      .left,
      .right {
        width: 50%;
        color: #cb3a35;
        line-height: 100rpx;
        text-align: center;
      }
      .left {
        border-right: 2rpx solid #f0f0f0;
        color: #000;
      }
    }
  }
}
.on {
  border-color: #cb3a35 !important;
  color: #cb3a35 !important;
  position: relative;
  overflow: hidden;
  &::after {
    content: "";
    width: 18px;
    height: 18px;
    background: #cb3a35;
    position: absolute;
    right: -9px;
    bottom: -9px;
    transform: rotate(45deg);
    z-index: 1;
  }
  &::before {
    box-sizing: content-box;
    content: "";
    border: 1px solid #fff;
    border-left: 0;
    border-top: 0;
    height: 4px;
    position: absolute;
    right: 3px;
    bottom: 2px;
    transform: rotate(45deg) scaleY(1);
    width: 2px;
    transition: transform 0.15s ease-in 0.05s;
    transform-origin: center;
    z-index: 2;
  }
}
.btn-on {
  background: #cb3a35;
  color: #fff;
}
</style>