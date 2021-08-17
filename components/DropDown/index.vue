<template>
  <view
    class="popup-body"
    v-show="visible"
  >
    <!-- 顶部混合过关选择 -->

    <view class="wrap">

      <view class="title">
        过关
      </view>

      <u-row gutter="20">
        <u-col
          span="4"
          v-for="item in dataTop"
          :key="item.id"
        >
          <view
            :class="{'on':item.id===checked.id}"
            class="col-item"
            @click="handleCol(item)"
          >{{item.label}}</view>
        </u-col>

      </u-row>

      <view class="title">
        单关
      </view>

      <u-row gutter="20">
        <u-col
          span="4"
          v-for="item in dataBot"
          :key="item.id"
        >
          <view
            :class="{'on':item.id===checked.id}"
            class="col-item"
            @click="handleCol(item)"
          >{{item.label}}</view>
        </u-col>

      </u-row>
    </view>

  </view>
</template>

<script>
export default {
  props: {
    checked: {
      type: Object,
      default: {},
    },
  },
  data() {
    return {
      visible: false,
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
      dataBot: [
        {
          id: 6,
          label: "胜平负",
        },
        {
          id: 7,
          label: "让球胜平负",
        },
        {
          id: 8,
          label: "比分",
        },
        {
          id: 9,
          label: "总进球",
        },
        {
          id: 10,
          label: "半全场",
        },
      ],
    };
  },
  methods: {
    handleCol(item) {
      this.$emit("update:checked", item);
      this.visible = false;
    },
  },
};
</script>

<style scoped lang="scss">
.popup-body {
  position: fixed;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  z-index: 9;
  background: rgba(#000000, 0.1);
}
.wrap {
  position: absolute;
  top: 90rpx;
  left: 0;
  padding: 0 20rpx;
  width: 100%;
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
}
.on {
  background: #cb3a35;
  color: #fff !important;
  border: none !important;
}
</style>