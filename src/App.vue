<template>
  <div id="app">
    <router-view></router-view>
    <router-view name="footer"></router-view>
  </div>
</template>

<style lang="scss">
@import '@/lib/reset.scss';
html,body,#app{
  @include rect(100%,100%);
}
#app{
  @include flexbox();
  @include flex-direction(column);
  .container{
    @include flexbox();
    @include flex-direction(column);
    @include flex();
    @include rect(100%,auto);
    @include overflow();
    .search{
      @include background-color(#ccc);
      @include rect(80%,0.3rem);
      border-radius: 0.15rem;
      margin: 0.15rem;
    }
    .carousel{
      @include rect(100%,auto);
    }
    // .icon{
    //   @include flexbox();
    //   @include rect(100%,3rem);
    // }
    .gif{
      @include rect(100%,1rem);
    }
    .hehe{
      @include rect(100%,3rem);
    }
  }
  .footer{
    @include rect(100%,0.5rem);
    ul{
      @include rect(100%,100%);
      @include flexbox();
      li{
        @include flex();
        @include rect(auto,100%);
        @include flexbox();
        @include flex-direction(column);
        @include align-items();
        @include justify-content();
        span{
          @include font-size(0.2rem);
        }
        &.router-link-active{
          @include color(rgb(221, 40, 94));
        }
      }
    }
  }
}
</style>
