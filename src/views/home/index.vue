<template>
    <div class="container">
      <div class="search">
        <div class="text" @click='search'>搜索</div>
      </div>
      <van-swipe :autoplay="3000" indicator-color="white" class="carousel">
        <van-swipe-item v-for="(items,index) of bannerlist" :key='index'>
          <img :src="items" alt="">
        </van-swipe-item>
      </van-swipe>
      <div class="icon">
          <img src="https://goods4.juancdn.com/jas/181119/7/6/5bf2524bb6f8ea534d206f83_270x241.png?imageMogr2/quality/85!/format/png" alt="">
          <img src="https://goods8.juancdn.com/jas/181228/f/e/5c25bd0d33b08962a220f3a6_270x241.png?imageMogr2/quality/85!/format/png" alt="">
          <img src="https://goods2.juancdn.com/jas/180201/3/d/5a727415a9fcf8280d24465a_270x241.png?imageMogr2/quality/85!/format/png" alt="">
          <img src="https://goods4.juancdn.com/jas/180917/6/5/5b9f175033b08945a870ad21_270x241.png?imageMogr2/quality/85!/format/png" alt="">
      </div>
      <div class="gif">
        <a class="img">
          <img src="https://s2.juancdn.com/jas/190712/f/9/5d2820d133b0897c8d42e339_1080x330.gif" alt="">
        </a>
      </div>
      <div class="hehe">
          <a href=""  class="time-limited">
            <img src="https://s2.juancdn.com/jas/190715/6/3/5d2bcff433b0890ae55a3fb8_540x656.gif" alt="">
          </a>
          <a href="" class="clearance">
            <img src="https://goods4.juancdn.com/jas/190715/7/7/5d2bd04333b0890aef143b01_540x328.png?imageMogr2/quality/85!/format/png" alt="">
          </a>
          <a href="" class="free">
            <img src="https://goods6.juancdn.com/jas/190715/b/d/5d2bd066b6f8ea44eb25ff46_540x328.png?imageMogr2/quality/85!/format/png" alt="">
          </a>
      </div>
      <Prolist :prolist= "prolist"/>
    </div>
</template>
<script>
import Prolist from '@/components/common/Prolist.vue'
import Vue from 'vue'
import { Swipe, SwipeItem, Icon, List, PullRefresh } from 'vant'
Vue.use(Swipe).use(SwipeItem)
Vue.use(List)
Vue.use(Icon)
Vue.use(PullRefresh)
export default {
  data () {
    return {
      bannerlist: []
    }
  },
  components: {
    Prolist
  },
  methods: {
    search () {

    }
  },
  mounted () {
    fetch('https://www.daxunxun.com/banner')
      .then(res => res.json()).then(data => {
        // console.log(data)
        var arr = []
        data.map(items => {
          items = 'https://www.daxunxun.com' + items
          arr.push(items)
        })
        console.log(arr)
        this.bannerlist = arr
      })
  }
}
</script>
<style lang="scss">
@import '@/lib/reset.scss';
.container{
  @include flexbox();
  @include flex-direction(column);
  @include overflow;
  .search{
    .text{
      margin-left:0.1rem;
      font-size:10px;
      line-height: 0.3rem;
      border-radius:0.15rem;
    }
  }
  .van-swipe{
    height:1.5rem;
    .van-swipe__track{
      @include rect(100%,100%);
      .van-swipe-item{
        float: left;
        img{
          width: 100%;
        }
      }
    }
  }
  .carousel{
    height:1.5rem;
      .van-swipe__track{
        @include rect(100%,100%);
        img{
          @include rect(100%,100%);
        }
      }
  }
  .icon{
    // @include flexbox();
    img{
      @include rect(25%,auto);
    }
  }
  .gif{
    .img{
      display: block;
      @include rect(100%,100%);
      img{
        display: block;
        @include rect(100%,100%);
      }
    }
  }
  .hehe{
    .time-limited{
      float: left;
      display: block;
      @include rect(50%,auto);
      img{
        display: block;
        @include rect(100%,100%);
      }
    }
    .clearance{
      float: left;
      display: block;
      @include rect(50%,auto);
      img{
        display: block;
        @include rect(100%,auto);
      }
    }
    .free{
      float: left;
      display: block;
      @include rect(50%,auto);
      img{
        display: block;
        @include rect(100%,auto);
      }
    }
  }
}
</style>
