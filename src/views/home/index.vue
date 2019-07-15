<template>
    <div class="container">
      <div class="search">
        <div class="text" @click='search'>搜索</div>
      </div>
      <div class="carousel">
        <van-swipe :autoplay="3000" indicator-color="white">
          <van-swipe-item v-for="(items, index) of bannerlist" :key='index'>
            <img :src="items" alt="">
          </van-swipe-item>
        </van-swipe>
      </div>
      <div class="content">
        <div class="icon">
          <div>
            <span class="iconfont icon-shangchengcopy"></span>
            <p>最后疯抢</p>
          </div>
          <div>
            <span class="iconfont icon-kuanchuangyidianzishangwutubiaoshiliangsucai--"></span>
            <p>限时秒杀</p>
          </div>
          <div>
            <span class="iconfont icon-_fuzhi-"></span>
            <p>品牌特卖</p>
          </div>
          <div>
            <span class="iconfont icon-chaoshi"></span>
            <p>生活超市</p>
          </div>
        </div>
        <div class="clear">
          <a>
            <img src="https://s2.juancdn.com/jas/190712/f/9/5d2820d133b0897c8d42e339_1080x330.gif" alt="">
          </a>
        </div>
        <div class="data">
          <div class="time-limited">
            
          </div>
          <div class="clearance"></div>
          <div class="free"></div>
        </div>
      </div>
    </div>
</template>
<script>
import Vue from 'vue'
import { Swipe, SwipeItem } from 'vant'
Vue.use(Swipe).use(SwipeItem)
export default {
  data () {
    return {
      bannerlist: []
    }
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
  .search{
    @include rect(80%,0.3rem);
    border-radius: 0.15rem;
    margin: 0.15rem;
    .text{
      margin-left:0.1rem;
      font-size:10px;
      line-height: 0.3rem;
      border-radius:0.15rem;
    }
  }
  .carousel{
    // @include flexbox();
    .van-swipe{
      height: 1rem;
      @include overflow;
      .van-swipe__track{
        @include rect(100%,100%);
        @include flexbox();
        .van-swipe-item{
          @include rect(100%,100%);
          img{
            @include rect(100%,100%);
          }
        }
      }
    }
    img{
      width:100%
    }
  }
  .content{
    .icon{
      @include flexbox();
      @include rect(100%,20%);
      div{
        @include flex();
        @include rect(auto,100%);
        @include flexbox();
        @include flex-direction(column);
        @include align-items();
        @include justify-content();
        span{
          font-size: 30px;
        }
        p{
          font-size: 12px;
        }
      }
    }
    .clear{
      @include rect(100%,1rem);
      a{
        display: block;
        @include rect(100%,100%);
        img{
          display: block;
          @include rect(100%,100%);
        }
      }
    }
    .data{
      
    }
  }
}
</style>
