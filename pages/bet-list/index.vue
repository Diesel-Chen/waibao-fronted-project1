<template>
  <view>
    <u-navbar
      title="投注列表"
      title-color="#fff"
      title-size="32"
      :background="{
        backgroundColor:'#CB3A35'
      }"
      back-icon-color="#fff"
    >
    </u-navbar>

    <!-- 顶部区域 -->
    <view class="header">
      <view
        class="left"
        @click="handleAdd"
      >+ 添加赛事</view>
      <view
        class="right"
        @click="handleClear"
      >清空重选</view>
    </view>

    <!-- 中部赛事区域 -->

    <view class="content">
      <view
        class="item"
        v-for="item in checkList"
        :key="item.matchId"
        @click="handleClickRow(item)"
      >

        <view class="item-top">

          <view class="left">
            <u-icon
              @click.native.stop="handleDelete(item)"
              color="#DDDDDD"
              name="close-circle-fill"
              size="38"
            ></u-icon>
          </view>
          <view class="right">
            <text> {{item.homeTeamAbbName}}</text>
            <text>VS</text>
            <text> {{item.awayTeamAbbName}}</text>

          </view>
        </view>

        <view class="item-bottom">
          <view class="left">
            <view> {{item.matchNumStr.slice(2)}}</view>
            <view>{{item.matchWeek}}</view>
          </view>
          <view class="mid">让平</view>
          <view class="right">
            <text>
              胆
            </text>
          </view>
        </view>
      </view>
    </view>

    <!-- 底部区域 -->
    <view class="bottom">
      <view class="one">
        <view
          class="left"
          @click="show=!show"
        >
          <text>3串1</text>
          <u-icon
            name="arrow-down"
            size="24"
          ></u-icon>
        </view>

        <view class="mid">
          <text>倍</text>
          <u-number-box v-model="value"></u-number-box>
          <text>数</text>
        </view>
        <view class="right">
          <text>奖金优化</text>
          <u-icon
            name="arrow-right"
            size="24"
          ></u-icon>
        </view>
      </view>

      <view
        class="wrap"
        v-show="show"
      >

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

      </view>

      <view class="two">
        <view class="top">
          2注4元 预计奖金：52.89~87.22元
        </view>
        <view class="bot">
          预计奖金仅供参考，请以实际票为准
        </view>

      </view>
      <view class="three">
        <view class="left">
          <u-icon
            name="zhuanfa"
            color="#CB3A35"
            size="30"
            top="3"
          ></u-icon>

          <text>发布跟单</text>
        </view>
        <view class="right">确认投注</view>
      </view>
    </view>

    <SelectModal
      :visible.sync="visible"
      :data="data"
    />
  </view>

</template>

<script>
import SelectModal from "@/components/SelectModal";
export default {
  components: {
    SelectModal,
  },
  provide() {
    return {
      parent: this,
    };
  },
  data() {
    return {
      value: 1,
      show: false,
      visible: false,
      checked: {},
      data: {},
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
      checkList: [],
    };
  },
  onLoad({ query }) {
    const checkList = JSON.parse(decodeURIComponent(query));
    this.checkList = checkList;
  },
  methods: {
    handleClickRow(item) {
      this.data = item;
      this.visible = true;
    },

    // 单个表格点击
    handleClickCell(el, prop) {
      const index = this.checkList.findIndex(
        (item) => item.matchId === el.matchId
      );
      if (index === -1) {
        this.checkList.push({
          ...el,
          props: [prop],
        });
      } else {
        const pIndex = this.checkList[index].props.indexOf(prop);
        if (pIndex === -1) {
          this.checkList[index].props.push(prop);
        } else {
          this.checkList[index].props.splice(pIndex, 1);
          if (!this.checkList[index].props.length) {
            this.checkList.splice(index, 1);
          }
        }
      }
    },

    // 表格是否勾选
    isChecked(el, prop) {
      const item = this.checkList.find((item) => item.matchId === el.matchId);
      if (item) {
        const index = item.props.indexOf(prop);
        return index !== -1;
      }

      return false;
    },

    // 删除按钮
    handleDelete(item) {
      const index = this.checkList.findIndex(
        (el) => el.matchId === item.matchId
      );
      this.checkList.splice(index, 1);
    },

    // 添加赛事按钮
    handleAdd() {
      uni.navigateBack({
        delta: 1,
      });
    },

    handleClear() {
      uni.navigateTo({
        url: "/pages/events-list/index",
      });
    },

    //
    handleCol(item) {
      this.checked = item;
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  height: 80rpx;
  background: #fff;
  display: flex;
  justify-content: space-around;
  align-items: center;
  .left,
  .right {
    width: 200rpx;
    height: 60rpx;
    border: 2rpx solid #f0f0f0;
    border-radius: 4rpx;
    color: grey;
    line-height: 60rpx;
    text-align: center;
    font-size: 24rpx;
  }
}
.content {
  margin: 30rpx;
  font-size: 24rpx;
  .item {
    padding: 20rpx;
    background: #fff;
    border-bottom: 2rpx solid #f0f0f0;
    height: 145rpx;

    .item-top {
      padding-right: 100rpx;
      display: flex;
      .left {
        width: 100rpx;
      }
      .right {
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex: 1;
      }
    }
    .item-bottom {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding-top: 10rpx;
      .left,
      .right {
        width: 100rpx;
      }
      .left {
        line-height: 30rpx;
      }
      .right {
        display: flex;
        align-items: center;
        justify-content: flex-end;
        text {
          width: 60rpx;
          height: 60rpx;
          border: 2rpx solid #f0f0f0;
          color: #ddd;
          line-height: 60rpx;
          text-align: center;
          display: block;
        }
      }
      .mid {
        flex: 1;
        height: 60rpx;
        color: #cb3a35;
        line-height: 60rpx;
        text-align: center;
        background: #dddddd;
      }
    }
  }
}

.bottom {
  width: 100%;
  background: #fff;
  box-shadow: 0 4rpx 12rpx 0 rgba(#000000, 0.1);
  position: fixed;
  bottom: 0;
  left: 0;
  .one,
  .two {
    height: 80rpx;
    border-top: 2rpx solid #eee;
    text-align: center;
    line-height: 40rpx;
    .top {
      font-size: 26rpx;
      color: grey;
    }
    .bot {
      font-size: 24rpx;
      color: #dddddd;
    }
  }
  .one {
    display: flex;
    .left,
    .right {
      width: 200rpx;
      font-size: 28rpx;
      color: grey;
      line-height: 80rpx;
      text-align: center;
    }
    .mid {
      flex: 1;
      border-right: 2rpx solid #eee;
      border-left: 2rpx solid #eee;
      display: flex;
      justify-content: center;
      align-items: center;
      text {
        color: grey;
        padding: 0 10rpx;
      }
    }
  }
  .three {
    height: 100rpx;
    border-top: 2rpx solid #eee;
    display: flex;
    .left {
      flex: 1;
      line-height: 100rpx;
      color: #cb3a35;
      padding-left: 50rpx;
    }
    .right {
      width: 200rpx;
      background: #cb3a35;
      color: #fff;
      line-height: 100rpx;
      text-align: center;
    }
  }
}

.wrap {
  border-top: 2rpx solid #eee;
  padding: 0 20rpx;
  max-height: 80vh;
  height: 100%;
  overflow: scroll;
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