<template>
  <section class="profile">
    <HeaderTop title="我的"/>
    <section class="profile-number">
      <router-link :to="userInfo._id ? '/userinfo':'/login'" class="profile-link">
        <div class="profile_image">
          <i class="iconfont icon-pic"></i>
        </div>
        <div class="user-info">
          <p class="user-info-top" v-if="!userInfo.phone">{{userInfo.name || '登录/注册'}}</p>
          <p>
                <span class="user-icon">
                  <i class="iconfont icon-icon-phone"></i>
                </span>
            <span class="icon-mobile-number">{{userInfo.phone || '暂无绑定手机号'}}</span>
          </p>
        </div>
        <span class="arrow">
              <i class="iconfont icon-xiangyou"></i>
        </span>
      </router-link>
    </section>
    <section class="profile_info_data border-1px">
      <ul class="info_data_list">
        <a href="javascript:" class="info_data_link">
          <span class="info_data_top"><span>0.00</span>元</span>
          <span class="info_data_bottom">我的余额</span>
        </a>
        <a href="javascript:" class="info_data_link">
          <span class="info_data_top"><span>0</span>个</span>
          <span class="info_data_bottom">我的优惠</span>
        </a>
        <a href="javascript:" class="info_data_link">
          <span class="info_data_top"><span>0</span>分</span>
          <span class="info_data_bottom">我的积分</span>
        </a>
      </ul>
    </section>
    <section class="profile_my_order border-1px">
      <!-- 我的订单 -->
      <a href='javascript:' class="my_order">
        <span>
          <i class="iconfont icon-dingdan"></i>
        </span>
        <div class="my_order_div">
          <span>我的订单</span>
          <span class="my_order_icon">
                <i class="iconfont icon-xiangyou"></i>
          </span>
        </div>
      </a>
      <!-- 积分商城 -->
      <a href='javascript:' class="my_order">
            <span>
              <i class="iconfont icon-shangcheng"></i>
            </span>
        <div class="my_order_div">
          <span>积分商城</span>
          <span class="my_order_icon">
                <i class="iconfont icon-xiangyou"></i>
              </span>
        </div>
      </a>
      <!-- 硅谷外卖会员卡 -->
      <a href="javascript:" class="my_order">
            <span>
              <i class="iconfont icon-vip"></i>
            </span>
        <div class="my_order_div">
          <span>浙理外卖会员卡</span>
          <span class="my_order_icon">
                <i class="iconfont icon-xiangyou"></i>
              </span>
        </div>
      </a>
      <!-- 服务中心 -->
      <a href="javascript:" class="my_order">
            <span>
              <i class="iconfont icon-service"></i>
            </span>
        <div class="my_order_div">
          <span>服务中心</span>
          <span class="my_order_icon">
                <i class="iconfont icon-xiangyou"></i>
              </span>
        </div>
      </a>
    </section>
    <section class="profile_loginout" v-if="userInfo._id" @click="loginOut">
      <mt-button type="danger" class="btn_loginout">退出</mt-button>
    </section>
  </section>

</template>

<script>
  import HeaderTop from '../../components/HeaderTop/HeaderTop'
  import {mapState} from 'vuex'
  import { Toast,MessageBox  } from 'mint-ui';
  export default {
    computed:{
      ...mapState(['userInfo'])
    },

    methods:{
      loginOut(){
        MessageBox.confirm('确定要退出吗？','提示').then(
          action => {
            Toast({
              message: '退出成功',
              position: 'bottom',
              duration: 2000
            });
          }
        ).catch(  action => {
          Toast('取消')
        })
      }
    },

    components:{
      HeaderTop
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixins.styl"

  .profile //我的
    width 100%
    overflow hidden
    .profile-number
      margin-top 45.5px
      .profile-link
        clearFix()
        position relative
        display block
        background #02a774
        padding 20px 10px
        .profile_image
          float left
          width 60px
          height 60px
          overflow hidden
          border-radius 50%
          vertical-align top
          .icon-pic
            background #fff
            font-size 62px
        .user-info
          float left
          margin-top 8px
          margin-left 15px
          p
            font-weight: 700
            font-size 18px
            color #fff
            &.user-info-top
              padding-bottom 8px
            .user-icon
              display inline-block
              margin-left -15px
              margin-right 5px
              width 20px
              height 20px
              .icon-mobile
                font-size 30px
                vertical-align text-top
            .icon-mobile-number
              font-size 14px
              color #fff
        .arrow
          width 12px
          height 12px
          position absolute
          right 15px
          top 40%
          .icon-jiantou1
            color #fff
            font-size 5px
    .profile_info_data
      bottom-border-1px(#e4e4e4)
      width 100%
      background #fff
      overflow hidden
      .info_data_list
        clearFix()
        .info_data_link
          float left
          width 33%
          text-align center
          border-right 1px solid #f1f1f1
          .info_data_top
            display block
            width 100%
            font-size 14px
            color #333
            padding 15px 5px 10px
            span
              display inline-block
              font-size 30px
              color #f90
              font-weight 700
              line-height 30px
          .info_data_bottom
            display inline-block
            font-size 14px
            color #666
            font-weight 400
            padding-bottom 10px
        .info_data_link:nth-of-type(2)
          .info_data_top
            span
              color #ff5f3e
        .info_data_link:nth-of-type(3)
          border 0
          .info_data_top
            span
              color #6ac20b
    .profile_my_order
      top-border-1px(#e4e4e4)
      margin-top 10px
      background #fff
      .my_order
        display flex
        align-items center
        padding-left 15px
        >span
          display flex
          align-items center
          width 20px
          height 20px
          >.iconfont
            font-size 20px
          .icon-dingdan
            color #02a774
          .icon-shangcheng
            color #ff5f3e
          .icon-vip
            color #f90
          .icon-service
            color #02a774
        .my_order_div
          width 100%
          border-bottom 1px solid #f1f1f1
          padding 18px 10px 18px 0
          font-size 16px
          color #333
          display flex
          justify-content space-between
          span
            display block
            margin-left 10px
          .my_order_icon
            width 10px
            height 10px
            margin-right 10px
            .icon-xiangyou
              color #bbb
              font-size 20px
    .profile_loginout
      margin-top 30px
      box-sizing border-box
      padding 0 20px
      .btn_loginout
        width 100%
</style>
