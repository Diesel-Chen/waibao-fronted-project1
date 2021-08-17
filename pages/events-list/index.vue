<template>
  <view class="page-body">

    <u-navbar
      :background="{
        backgroundColor:'#CB3A35'
      }"
      back-icon-color="#fff"
    >

      <view
        class="nav-mid"
        @click="handleDropDown"
      >
        <text> {{checked.label}}</text>
        <u-icon
          name="arrow-down"
          color="#EEE"
          size="28"
        ></u-icon>
      </view>

      <view
        slot="right"
        class="nav-right"
      >

        <u-icon
          name="plus-circle"
          color="#EEE"
          size="38"
          @click="checkVisible=true"
          style="margin-right:10rpx;"
        ></u-icon>
        <u-icon
          name="list-dot"
          color="#EEE"
          size="38"
        ></u-icon>
      </view>

    </u-navbar>

    <uni-collapse>
      <uni-collapse-item
        :open="index===0"
        v-for="(item,index) in matchInfoList"
        :key="index"
      >
        <view class="event-content">

          <view
            class="event-item"
            v-for="(el,i) in item.subMatchList"
            :key="i"
          >
            <view class="item">
              <view class="item-left">
                <view>
                  {{el.matchNumStr.slice(2)}}
                </view>
                <view>
                  {{el.leagueAbbName}}
                </view>
                <view>
                  {{getEndTime(el.matchDate,el.matchTime,el.matchWeek)}}
                </view>
                <view
                  class="analyse"
                  @click="handleAnalyse(el)"
                >
                  分析
                </view>
              </view>
              <view class="item-right">
                <view class="right-head">
                  <view>
                    {{el.homeTeamAbbName}}
                  </view>
                  <view>
                    VS
                  </view>
                  <view>
                    {{el.awayTeamAbbName}}
                  </view>
                </view>

                <view class="right-bottom">
                  <view class="left">
                    <view class="u-td-view">
                      {{el.had.goalLine || 0}}
                    </view>
                    <view
                      class="u-td-view"
                      :style="{
                      background:el.hhad.goalLine < 0 ? '#9d9df9' : '#EA8784'
                    }"
                    >{{el.hhad.goalLine}}</view>
                  </view>
                  <u-table border-color="#eee">
                    <u-tr>

                      <u-td
                        width="85%"
                        class="td-body"
                      >
                        <u-tr>
                          <u-td>
                            <view
                              class="checked-item"
                              @click="handleClickCell(el,'had.h')"
                              :class="{'on':isChecked(el,'had.h')}"
                            >胜 {{el.had.h}}</view>
                          </u-td>
                          <u-td>
                            <view
                              class="checked-item"
                              @click="handleClickCell(el,'had.d')"
                              :class="{'on':isChecked(el,'had.d')}"
                            >
                              平 {{el.had.d}}</view>
                          </u-td>
                          <u-td>
                            <view
                              class="checked-item"
                              @click="handleClickCell(el,'had.a')"
                              :class="{'on':isChecked(el,'had.a')}"
                            >
                              负 {{el.had.a}}</view>
                          </u-td>
                        </u-tr>
                        <u-tr>
                          <u-td>
                            <view
                              class="checked-item"
                              @click="handleClickCell(el,'hhad.h')"
                              :class="{'on':isChecked(el,'hhad.h')}"
                            >
                              胜 {{el.hhad.h}}</view>
                          </u-td>
                          <u-td>
                            <view
                              class="checked-item"
                              @click="handleClickCell(el,'hhad.d')"
                              :class="{'on':isChecked(el,'hhad.d')}"
                            >
                              平 {{el.hhad.d}}</view>
                          </u-td>
                          <u-td>
                            <view
                              class="checked-item"
                              @click="handleClickCell(el,'hhad.a')"
                              :class="{'on':isChecked(el,'hhad.a')}"
                            >
                              负 {{el.hhad.a}}</view>
                          </u-td>
                        </u-tr>
                      </u-td>

                      <u-td
                        class="more"
                        width="15%"
                      >
                        <view
                          @click="handleMoreOption(el)"
                          class="checked-item"
                          :class="{'on':isCheckedMore(el)}"
                        >
                          <view>更多</view>
                          <view>选项</view>
                        </view>

                      </u-td>
                    </u-tr>

                  </u-table>
                </view>
              </view>
            </view>

            <view
              v-show="el.show"
              class="analyse-content"
            >
              <view class="line">
                <text class="title">历史交锋</text>
                <text>近1次交锋，纳塔尔ABC</text>
                <text style="color:#CB3A35">0胜</text>
                <text style="color:#9D9DF9">0平</text>
                <text style="color:#509423">1负</text>
              </view>
              <view class="line">
                <text class="title">近期战绩</text>
                <text>主队</text>
                <text style="color:#CB3A35">13胜</text>
                <text style="color:#9D9DF9">9平</text>
                <text style="color:#509423">1负</text>
                <text>客队</text>
                <text style="color:#CB3A35">1胜</text>
                <text style="color:#9D9DF9">8平</text>
                <text style="color:#509423">1负</text>
              </view>
              <view class="line">
                <text class="title">联赛排名</text>
                <text>暂无数据</text>
              </view>
              <view class="bot">
                <text>
                  详细赛事分析
                </text>
                <u-icon
                  name="arrow-right"
                  size="26"
                ></u-icon>
              </view>
            </view>

          </view>

        </view>
        <view
          slot="title"
          class="collapse-item-title"
        >
          <span>{{item.businessDate}}</span>
          <span>{{item.weekday}}</span>
          <span>共{{item.matchCount}}场比赛</span>
        </view>
      </uni-collapse-item>

    </uni-collapse>

    <SelectModal
      :visible.sync="visible"
      :data="data"
    />
    <DropDown
      ref="drop"
      :visible="dropVisible"
      :checked.sync="checked"
    />
    <CheckBoxList :visible.sync="checkVisible" />

    <view class="bottom-fixed">
      <view class="delete">
        <u-icon
          @click="handleClear"
          name="trash"
          color="grey"
          size="38"
        ></u-icon>
      </view>
      <view class="text">
        {{checkList.length > 1 ? `您已选择${checkList.length}场比赛` : `非单关至少选择2场比赛`}}
      </view>
      <view class="btn">
        <text @click="handleConfirm">确定</text>
      </view>
    </view>

  </view>
</template>

<script>
import SelectModal from "@/components/SelectModal";
import DropDown from "@/components/DropDown";
import CheckBoxList from "@/components/CheckBoxList";
export default {
  components: {
    SelectModal,
    DropDown,
    CheckBoxList,
  },
  provide() {
    return {
      parent: this,
    };
  },
  data() {
    return {
      dropVisible: false,
      matchInfoList: [],
      visible: false,
      data: {},
      checkVisible: false,
      checked: {
        id: 0,
        label: "混合过关",
      },

      checkList: [],
    };
  },
  watch: {
    checkList: {
      handler(val) {
        console.log(val);
      },
      deep: true,
    },
  },
  onLoad() {
    this.init();
  },
  methods: {
    handleConfirm() {
      const query = encodeURIComponent(JSON.stringify(this.checkList));
      uni.navigateTo({
        url: `/pages/bet-list/index?query=${query}`,
      });
    },

    // 清空按钮
    handleClear() {
      this.checkList = [];
    },

    // 分析按钮
    handleAnalyse(el) {
      this.$set(el, "show", !el.show);
    },

    // 更多选项是否勾选
    isCheckedMore(el) {
      const item = this.checkList.find((item) => item.matchId === el.matchId);
      if (item) {
        return item.props.some((prop) => {
          return (
            prop.includes("hafu") ||
            prop.includes("ttg") ||
            prop.includes("crs")
          );
        });
      }

      return false;
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

    handleDropDown() {
      this.$refs["drop"].visible = true;
    },

    // 更多选项
    handleMoreOption(data) {
      this.data = data;
      this.visible = true;
    },

    // 是否已经结束
    isOver(date, time) {
      return new Date(Date.parse(`${date} ${time}`)) < new Date();
    },

    // 获取比赛结束时间
    getEndTime(date, time, week) {
      const isOver = this.isOver(date, time);

      if (!isOver) {
        if (week === "周六" || week === "周日") {
          return "23:00";
        } else {
          return "22:00";
        }
      }
      return time;
    },

    init() {
      uni.request({
        url: "https://webapi.sporttery.cn/gateway/jc/football/getMatchCalculatorV1.qry?poolCode=&channel=c", //仅为示例，并非真实接口地址。
        success: ({ data }) => {
          const { matchInfoList, matchDateList } = data?.value;
          matchInfoList.map((item) => {
            matchDateList.map((el) => {
              if (item.weekday === el.businessDateCn) {
                item.businessDate = el.businessDate;
              }
            });
          });

          this.matchInfoList = matchInfoList;
        },
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.u-table,
.u-td {
  border-width: 2rpx;
  font-size: 24rpx !important;
  color: grey !important;
  padding: 0 !important;
}
.u-td,
.u-td-view {
  height: 70rpx;
  .checked-item {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
}
.u-tr,
.td-body {
  height: 140rpx;
}
.td-body {
  border: none !important;
}
.more {
  height: 140rpx;
}
::v-deep .u-slot-content {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.nav-mid {
  background: #cb3a35;
  color: #eee;
  font-size: 24rpx;
  font-size: 32rpx;
  text {
    padding: 0 10rpx;
  }
}
.nav-right {
  padding-right: 30rpx;
}
.collapse-item-title {
  font-size: 24rpx;
  height: 80rpx;
  line-height: 80rpx;

  span {
    padding: 0 20rpx;
  }
}
.event-content {
  .item {
    display: flex;
    background: #f8f8f8;
    border-top: 1px solid #dee1e6;
    font-size: 22rpx;
    padding: 20rpx 0;
    color: gray;

    .item-left {
      width: 20%;
      text-align: center;
      .analyse {
        color: #9d9df9;
      }
      view {
        padding: 8rpx 0;
      }
    }
    .item-right {
      width: 80%;
      .right-head {
        display: flex;
        justify-content: space-around;
        padding: 0 20rpx 10rpx 0;
      }
      .right-bottom {
        display: flex;
        padding: 0 20rpx 0 0;
        .left {
          padding-right: 10rpx;
          display: flex;
          flex-direction: column;
          justify-content: space-around;
          align-items: center;
          .u-td-view {
            width: 46rpx;
            height: 46rpx;
            border-radius: 46rpx;
            text-align: center;
            line-height: 46rpx;
            &:nth-child(2) {
              color: #fff;
            }
          }
        }
      }
    }
  }
  .analyse-content {
    background: #eaeaea;
    font-size: 22rpx;
    .line {
      padding: 10rpx 15rpx;
      border-bottom: 2rpx solid #e4e4e4;
      text {
        color: #b4b4b4;
      }
      .title {
        color: #000;
        padding-right: 20rpx;
      }
    }
    .bot {
      text-align: center;
      padding: 10rpx 0;
    }
  }
}
.bottom-fixed {
  height: 100rpx;
  position: fixed;
  width: 100%;
  border-top: 2rpx solid #ebeef5;
  box-shadow: 0 4rpx 24rpx 0 rgba(#000000, 0.1);
  bottom: 0;
  left: 0;
  z-index: 99;
  background: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  .delete,
  .btn {
    width: 150rpx;
    text-align: center;
  }
  .delete {
    width: 100rpx;
    border-right: 2rpx solid #ebeef5;
    height: 100%;
    line-height: 100rpx;
  }
  .btn {
    text {
      display: block;
      background: #cb3a35;
      border-radius: 4rpx;
      color: #fff;
      width: 130rpx;
      height: 70rpx;
      line-height: 70rpx;
    }
  }
  .text {
    flex: 1;
    text-align: center;
    color: gray;
    font-size: 24rpx;
  }
}
.on {
  background: #cb3a35;
  color: #fff !important;
}
</style>