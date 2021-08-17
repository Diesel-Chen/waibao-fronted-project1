<template>
  <view
    class="modal-mask"
    v-show="visible"
  >
    <view
      class="modal"
      v-if="visible"
    >
      <view class="head">
        <view> {{data.homeTeamAbbName}}</view>
        <view>VS</view>
        <view> {{data.awayTeamAbbName}}</view>
      </view>
      <view class="mid">

        <scroll-view
          scroll-y
          class="scroll-Y"
        >
          <view class="title">
            让球胜平负
          </view>
          <view class="cell-content">
            <u-table border-color="#eee">
              <u-tr>
                <u-td width='10%'>
                  <view>{{data.had.goalLine || 0}}</view>
                </u-td>
                <u-td>
                  <view
                    class="checked-item"
                    @click="parent.handleClickCell(data,'had.h')"
                    :class="{'cellOn':parent.isChecked(data,'had.h')}"
                  >
                    <view>胜</view>
                    <view>{{data.had.h}}</view>
                  </view>
                </u-td>
                <u-td>
                  <view
                    class="checked-item"
                    @click="parent.handleClickCell(data,'had.d')"
                    :class="{'cellOn':parent.isChecked(data,'had.d')}"
                  >
                    <view>平</view>
                    <view>{{data.had.d}}</view>
                  </view>
                </u-td>
                <u-td>
                  <view
                    class="checked-item"
                    @click="parent.handleClickCell(data,'had.a')"
                    :class="{'cellOn':parent.isChecked(data,'had.a')}"
                  >
                    <view>负</view>
                    <view>{{data.had.a}}</view>
                  </view>
                </u-td>
              </u-tr>
            </u-table>
          </view>
          <view class="title">
            胜平负
          </view>
          <view class="cell-content">
            <u-table border-color="#eee">
              <u-tr>
                <u-td width='10%'>
                  <view>{{data.hhad.goalLine}}</view>
                </u-td>
                <u-td>
                  <view
                    class="checked-item"
                    @click="parent.handleClickCell(data,'hhad.h')"
                    :class="{'cellOn':parent.isChecked(data,'hhad.h')}"
                  >
                    <view>胜</view>
                    <view>{{data.hhad.h}}</view>
                  </view>
                </u-td>
                <u-td>
                  <view
                    class="checked-item"
                    @click="parent.handleClickCell(data,'hhad.d')"
                    :class="{'cellOn':parent.isChecked(data,'hhad.d')}"
                  >
                    <view>平</view>
                    <view>{{data.hhad.d}}</view>
                  </view>
                </u-td>
                <u-td>
                  <view
                    class="checked-item"
                    @click="parent.handleClickCell(data,'hhad.a')"
                    :class="{'cellOn':parent.isChecked(data,'hhad.a')}"
                  >
                    <view>负</view>
                    <view>{{data.hhad.a}}</view>
                  </view>
                </u-td>
              </u-tr>
            </u-table>
          </view>
          <view class="title">
            <text class="badge">单</text>
            <text>比分</text>
          </view>
          <view class="">
            <u-table border-color="#eee">
              <u-tr class="win">

                <u-td
                  class="more"
                  width="40rpx"
                >
                  <view style="color:#cb3a35;">主胜</view>
                </u-td>
                <u-td class="td-body">
                  <u-tr>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s01s00')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s01s00')}">
                        <view>1:0</view>
                        <view class="text-num">{{data.crs.s01s00}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s02s00')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s02s00')}">
                        <view>2:0</view>
                        <view class="text-num">{{data.crs.s02s00}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s02s01')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s02s01')}">
                        <view>2:1</view>
                        <view class="text-num">{{data.crs.s02s01}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s03s00')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s03s00')}">
                        <view>3:0</view>
                        <view class="text-num">{{data.crs.s03s00}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s03s01')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s03s01')}">
                        <view>3:1</view>
                        <view class="text-num">{{data.crs.s03s01}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                  <u-tr>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s03s02')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s03s02')}">
                        <view>3:2</view>
                        <view class="text-num">{{data.crs.s03s02}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s04s00')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s04s00')}">
                        <view>4:0</view>
                        <view class="text-num">{{data.crs.s04s00}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s04s01')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s04s01')}">
                        <view>4:1</view>
                        <view class="text-num">{{data.crs.s04s01}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s04s02')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s04s02')}">
                        <view>4:2</view>
                        <view class="text-num">{{data.crs.s04s02}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s05s00')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s05s00')}">
                        <view>5:0</view>
                        <view class="text-num">{{data.crs.s05s00}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                  <u-tr>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s05s01')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s05s01')}">
                        <view>5:1</view>
                        <view class="text-num">{{data.crs.s05s01}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s05s02')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s05s02')}">
                        <view>5:2</view>
                        <view class="text-num">{{data.crs.s05s02}}</view>
                      </view>
                    </u-td>
                    <u-td width="60%">
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s1sh')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s1sh')}">
                        <view>胜其它</view>
                        <view class="text-num">{{data.crs.s1sh}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                </u-td>

              </u-tr>

              <u-tr>
                <u-td width="40rpx">
                  <view style="color:#0000FF">平</view>
                </u-td>
                <u-td class="td-body">
                  <u-tr>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s00s00')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s00s00')}">
                        <view>0:0</view>
                        <view class="text-num">{{data.crs.s00s00}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s01s01')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s01s01')}">
                        <view>1:1</view>
                        <view class="text-num">{{data.crs.s01s01}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s02s02')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s02s02')}">
                        <view>2:2</view>
                        <view class="text-num">{{data.crs.s02s02}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s03s03')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s03s03')}">
                        <view>3:3</view>
                        <view class="text-num">{{data.crs.s03s03}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s1sd')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s1sd')}">
                        <view>平其它</view>
                        <view class="text-num">{{data.crs.s1sd}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                </u-td>
              </u-tr>

              <u-tr class="win">

                <u-td
                  class="more"
                  width="40rpx"
                >
                  <view style="color:#509423">主负</view>
                </u-td>
                <u-td class="td-body">
                  <u-tr>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s00s01')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s00s01')}">
                        <view>0:1</view>
                        <view class="text-num">{{data.crs.s00s01}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s00s02')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s00s02')}">
                        <view>0:2</view>
                        <view class="text-num">{{data.crs.s00s02}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s01s02')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s01s02')}">
                        <view>1:2</view>
                        <view class="text-num">{{data.crs.s01s02}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s00s03')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s00s03')}">
                        <view>0:3</view>
                        <view class="text-num">{{data.crs.s00s03}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s01s03')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s01s03')}">
                        <view>1:3</view>
                        <view class="text-num">{{data.crs.s01s03}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                  <u-tr>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s02s03')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s02s03')}">
                        <view>2:3</view>
                        <view class="text-num">{{data.crs.s02s03}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s00s04')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s00s04')}">
                        <view>0:4</view>
                        <view class="text-num">{{data.crs.s00s04}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s01s04')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s01s04')}">
                        <view>1:4</view>
                        <view class="text-num">{{data.crs.s01s04}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'s02s04')"
                        :class="{'cellOn':parent.isChecked(data,'s02s04')}">
                        <view>2:4</view>
                        <view class="text-num">{{data.crs.s02s04}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s00s05')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s00s05')}">
                        <view>0:5</view>
                        <view class="text-num">{{data.crs.s00s05}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                  <u-tr>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s01s05')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s01s05')}">
                        <view>1:5</view>
                        <view class="text-num">{{data.crs.s01s05}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s02s05')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s02s05')}">
                        <view>2:5</view>
                        <view class="text-num">{{data.crs.s02s05}}</view>
                      </view>
                    </u-td>
                    <u-td width="60%">
                      <view
                      class="checked-item"
                        @click="parent.handleClickCell(data,'crs.s1sa')"
                        :class="{'cellOn':parent.isChecked(data,'crs.s1sa')}">
                        <view>负其它</view>
                        <view class="text-num">{{data.crs.s1sa}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                </u-td>

              </u-tr>

            </u-table>
          </view>

          <view class="title">
            <text class="badge">单</text>
            <text>总进球</text>
          </view>
          <view>

            <u-table border-color="#eee">
              <u-tr>
                <u-td
                  width="40rpx"
                  class="total-td"
                >
                  <view>总进球</view>
                </u-td>
                <u-td class="td-body">
                  <u-tr>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'ttg.s0')"
                        :class="{'cellOn':parent.isChecked(data,'ttg.s0')}"
                      >
                        <view>0 球</view>
                        <view class="text-num">{{data.ttg.s0}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'ttg.s1')"
                        :class="{'cellOn':parent.isChecked(data,'ttg.s1')}"
                      >
                        <view>1 球</view>
                        <view class="text-num">{{data.ttg.s1}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'ttg.s2')"
                        :class="{'cellOn':parent.isChecked(data,'ttg.s2')}"
                      >
                        <view>2 球</view>
                        <view class="text-num">{{data.ttg.s2}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'ttg.s3')"
                        :class="{'cellOn':parent.isChecked(data,'ttg.s3')}"
                      >
                        <view>3 球</view>
                        <view class="text-num">{{data.ttg.s3}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                  <u-tr>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'ttg.s4')"
                        :class="{'cellOn':parent.isChecked(data,'ttg.s4')}"
                      >
                        <view>4 球</view>
                        <view class="text-num">{{data.ttg.s4}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'ttg.s5')"
                        :class="{'cellOn':parent.isChecked(data,'ttg.s5')}"
                      >
                        <view>5 球</view>
                        <view class="text-num">{{data.ttg.s5}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'ttg.s6')"
                        :class="{'cellOn':parent.isChecked(data,'ttg.s6')}"
                      >
                        <view>6 球</view>
                        <view class="text-num">{{data.ttg.s6}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'ttg.s7')"
                        :class="{'cellOn':parent.isChecked(data,'ttg.s7')}"
                      >
                        <view>7+</view>
                        <view class="text-num">{{data.ttg.s7}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                </u-td>

              </u-tr>

            </u-table>
          </view>
          <view class="title">
            <text class="badge">单</text>
            <text>半全场</text>
          </view>
          <view>

            <u-table border-color="#eee">
              <u-tr>
                <u-td
                  width="40rpx"
                  class="win"
                >
                  <view>半全场</view>
                </u-td>
                <u-td class="td-body">
                  <u-tr>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'hafu.hh')"
                        :class="{'cellOn':parent.isChecked(data,'hafu.hh')}"
                      >
                        <view>胜/胜</view>
                        <view class="text-num">{{data.hafu.hh}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'hafu.ad')"
                        :class="{'cellOn':parent.isChecked(data,'hafu.ad')}"
                      >
                        <view>胜/平</view>
                        <view class="text-num">{{data.hafu.ad}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        @click="parent.handleClickCell(data,'hafu.ha')"
                        :class="{'cellOn':parent.isChecked(data,'hafu.ha')}"
                      >
                        <view>胜/负</view>
                        <view class="text-num">{{data.hafu.ha}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                  <u-tr>
                    <u-td>
                      <view
                        class="checked-item"
                        :class="{'cellOn':parent.isChecked(data,'hafu.dh')}"
                        @click="parent.handleClickCell(data,'hafu.dh')"
                      >
                        <view>平/胜</view>
                        <view class="text-num">{{data.hafu.dh}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        :class="{'cellOn':parent.isChecked(data,'hafu.dd')}"
                        @click="parent.handleClickCell(data,'hafu.dd')"
                      >
                        <view>平/平</view>
                        <view class="text-num">{{data.hafu.dd}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        :class="{'cellOn':parent.isChecked(data,'hafu.da')}"
                        @click="parent.handleClickCell(data,'hafu.da')"
                      >
                        <view>平/负</view>
                        <view class="text-num">{{data.hafu.da}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                  <u-tr>
                    <u-td>
                      <view
                        class="checked-item"
                        :class="{'cellOn':parent.isChecked(data,'hafu.ah')}"
                        @click="parent.handleClickCell(data,'hafu.ah')"
                      >
                        <view>负/胜</view>
                        <view class="text-num">{{data.hafu.ah}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        :class="{'cellOn':parent.isChecked(data,'hafu.hd')}"
                        @click="parent.handleClickCell(data,'hafu.hd')"
                      >
                        <view>负/平</view>
                        <view class="text-num">{{data.hafu.hd}}</view>
                      </view>
                    </u-td>
                    <u-td>
                      <view
                        class="checked-item"
                        :class="{'cellOn':parent.isChecked(data,'hafu.aa')}"
                        @click="parent.handleClickCell(data,'hafu.aa')"
                      >
                        <view>负/负</view>
                        <view class="text-num">{{data.hafu.aa}}</view>
                      </view>
                    </u-td>
                  </u-tr>
                </u-td>

              </u-tr>

            </u-table>
          </view>
        </scroll-view>

      </view>
      <view class="bottom">
        <view @click="cancel">取消</view>
        <view @click="cancel">确定</view>
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
    data: {
      type: Object,
      default: {},
    },
  },

  inject: ["parent"],
  watch: {
    data(val) {
      console.log(val);
    },
  },

  methods: {
    // 关闭弹框
    cancel() {
      this.$emit("update:visible", false);
    },
  },
};
</script>

<style lang="scss" scoped>
.modal-mask {
  width: 100vw;
  height: 100vh;
  background: rgba(#000000, 0.2);
  position: fixed;
  z-index: 9999;
  left: 0;
  top: 0;
  .modal {
    width: 90vw;
    height: 90vh;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    background: #fff;
    border-radius: 4rpx;
    .head,
    .bottom {
      height: 100rpx;
      line-height: 100rpx;
      display: flex;
      justify-content: space-around;
      padding: 0 70rpx;
      border-bottom: 2rpx solid #eee;
    }
    .mid {
      padding: 20rpx 20rpx 100rpx 20rpx;
      font-size: 24rpx;
      .scroll-Y {
        height: calc(90vh - 220rpx);
      }
      .title {
        padding: 20rpx 0;
      }
      .cell-content {
        padding: 20rpx 0;
      }
    }
    .bottom {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      border-top: 2rpx solid #eee;
      padding: 0;
      background: #fff;
      view {
        flex: 1;
        text-align: center;
      }
      .confirm {
        color: #CB3A35;
        border-left: 2rpx solid #eee;
      }
    }
  }
}
.u-table,
.u-td {
  border-width: 2rpx;
  font-size: 24rpx !important;
}
.u-td {
  height: 100rpx;
  padding: 0 !important;
  .checked-item {
    height: 100%;
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
}
.win {
  height: 300rpx;
  .more {
    height: 100%;
  }
}
.td-body {
  height: 100%;
  border: none !important;
  padding: 0 !important;
}
.total-td {
  height: 200rpx;
}
.text-num {
  color: #888;
}
.badge {
  background: #cb3a35;
  color: #fff;
  display: inline-block;
  width: 30rpx;
  height: 30rpx;
  text-align: center;
  line-height: 30rpx;
  margin-right: 10rpx;
}
.cellOn {
  background: #CB3A35;
  color: #fff !important;
  .text-num {
    color: #fff;
  }
}
</style>