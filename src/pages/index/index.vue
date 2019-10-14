<template>
  <div class="indexContainer">
    <img v-if="isShow" :src="userInfo.avatarUrl" alt="">
    <button
      v-else
      class="btn"
      open-type="getUserInfo"
      @getuserinfo="getUserInfo"
      lang="zh_CN"
      >
      点击获取用户登录的信息
    </button>
    <p class="username">hello {{userInfo.nickName}}</p>
    <div @tap="toDetail" class="goStudy">
      <!-- 不想上冒泡的写法  <p @tap.stop="handleChild">开启小程序之旅</p>  -->
      <p >开启小程序之旅</p> 
    </div>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      userInfo: {},
      isShow: false
    }
  },

  components: {
    card
  },

  onLoad () {
    console.log('---wx onLoad---')
  },
  beforeMount () {
    console.log('beforeunt')
    this.handleGetUserInfo()
  },
  methods: {
    handleGetUserInfo () {
      wx.getUserInfo({
        success: res => {
          this.userInfo = res.userInfo
          console.log(this.userInfo)
          this.isShow = true
        },
        fail: () => {
          console.log('获取失败')
        },
        complete: () => {}
      })
    },
    getUserInfo (data) {
      console.log(data)
      if (data.mp.detail.rawData) {
        this.handleGetUserInfo()
      }
    },
    toDetail () {
      // console.log('触发了')
      wx.navigateTo({ url: '/pages/list/main' })
      // wx.switchTab({ url: '/pages/list/main' })
    }
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
  page {
    background: #8ed145;
  }

  .indexContainer{
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .index_img {
    width: 200rpx;
    height: 200rpx;
    border-radius: 100rpx !important;
    margin: 100rpx 0;
  }

  .username{
    font-size: 40rpx;
    font-weight: bold;
    margin: 100rpx 0;
  }

  .goStudy{
    width: 220rpx;
    height: 80rpx;
    border: 1rpx solid #eee;
    font-size: 24rpx;
    line-height: 80rpx;
    text-align: center;
    border-radius: 10rpx;
  }

  .btn{
    width: 300rpx;
    height: 300rpx;
    border-radius: 150rpx;
    margin: 100rpx 0;
    line-height: 300rpx;
    text-align: center;
    font-size: 26rpx;
  }
</style>
