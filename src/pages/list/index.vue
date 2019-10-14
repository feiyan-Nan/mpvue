<template>
  <div class="listContainer">
    <swiper autoplay interval="1500" circular indicator-dots indicator-color="pink" indicator-active-color="green">
        <swiper-item>
            <img src="/static/images/detail/carousel/01.jpg" alt="">
        </swiper-item>
        <swiper-item>
            <img src="/static/images/detail/carousel/02.jpg" alt="">
        </swiper-item>
        <swiper-item>
            <img src="/static/images/detail/carousel/03.jpg" alt="">
        </swiper-item>
        <swiper-item>
            <img src="/static/images/detail/carousel/04.jpg" alt="">
        </swiper-item>
    </swiper>
    <button @tap="getStore">点</button>
    <div>
      <ListTmp v-for="(item, index) in listTmp" :key="index" :item="item" :index="index"></ListTmp>
    </div>
  </div>
</template>

<script>
import {mapState} from 'vuex'
import ListTmp from '@/pages/list_template/list_template.vue'

export default {
  data () {
    return {
      userInfo: {},
      isShow: false,
      aa: this.$store.state
    }
  },
  components: {ListTmp},
  onLoad () {
    console.log('---wx onLoad---')
  },
  beforeMount () {
    // 分发action 修改状态
    this.$store.dispatch('getList')
  },
  computed: {
    // 映射状态到本组件
    ...mapState(['listTmp'])
  },
  methods: {
    getStore () {
      console.log(this.aa)
    }
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
    .listContainer swiper{
        width: 100%;
        height: 400rpx;
    }
    .listContainer swiper img{
        width: 100%;
        height: 100%;
    }
</style>
