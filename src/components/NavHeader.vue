<template>
  <div class="header">
    <div class="nav_topbar">
      <div class="container">
        <div class="topbar_menu">
          <a href="javascript:;">小米商城</a>
          <a href="javascript:;">MUI</a>
          <a href="javascript:;">云服务</a>
          <a href="javascript:;">协议规则</a>
        </div>
        <div class="topbar_user">
          <a href="javascript:;" v-if="username">{{username}}</a>
          <a href="javascript:;" v-if="!username" @click="login">登录</a>
         <a href="javascript:;">我的订单</a>
          <a href="javascript:;" v-if="username">注册</a>
          <a href="javascript:;" class="my_cart" @click="goToCart"
            ><span class="icon_cart"></span>购物车</a
          >
        </div>
      </div>
    </div>
    <div class="nav_header">
      <div class="container">
        <div class="header_logo"><a href="/#/index"></a></div>
        <div class="header_menu">
          <div class="items_menu">
            <span>小米手机</span>
            <div class="children">
              <ul>
                <li class="product" v-for="(item,index) in phoneList" :key="index">
                  <a :href="`/#/product/${item.id}`" target="_blank"
                    ><div class="pro_imgs">
                      <img :src="item.mainImage" :alt="item.subtitle" />
                    </div>
                    <div class="pro_name">{{item.name}}</div>
                    <div class="pro_price">{{item.price | currency}}</div></a
                  >
                </li>
              </ul>
            </div>
          </div>
          <div class="items_menu">
            <span>红米手机</span>
            <div class="children"></div>
          </div>
          <div class="items_menu">
            <span>电视</span>
            <div class="children">
              <ul>
                <li class="product">
                  <a href="" target="_blank"
                    ><div class="pro_imgs">
                      <img src="/imgs/nav-img/nav-3-1.jpg" alt="" />
                    </div>
                    <div class="pro_name">小米CC9</div>
                    <div class="pro_price">1799元</div></a
                  >
                </li>
                <li class="product">
                  <a href="" target="_blank"
                    ><div class="pro_imgs">
                      <img src="/imgs/nav-img/nav-3-6.png" alt="" />
                    </div>
                    <div class="pro_name">小米CC9</div>
                    <div class="pro_price">1799元</div></a
                  >
                </li>
                <li class="product">
                  <a href="" target="_blank"
                    ><div class="pro_imgs">
                      <img src="/imgs/nav-img/nav-3-3.png" alt="" />
                    </div>
                    <div class="pro_name">小米CC9</div>
                    <div class="pro_price">1799元</div></a
                  >
                </li>
                <li class="product">
                  <a href="" target="_blank"
                    ><div class="pro_imgs">
                      <img src="/imgs/nav-img/nav-3-4.jpg" alt="" />
                    </div>
                    <div class="pro_name">小米CC9</div>
                    <div class="pro_price">1799元</div></a
                  >
                </li>
                <li class="product">
                  <a href="" target="_blank"
                    ><div class="pro_imgs">
                      <img src="/imgs/nav-img/nav-3-2.jpg" alt="" />
                    </div>
                    <div class="pro_name">小米CC9</div>
                    <div class="pro_price">1799元</div></a
                  >
                </li>
                <li class="product">
                  <a href="" target="_blank"
                    ><div class="pro_imgs">
                      <img src="/imgs/nav-img/nav-3-5.jpg" alt="" />
                    </div>
                    <div class="pro_name">小米CC9</div>
                    <div class="pro_price">1799元</div></a
                  >
                </li>
              </ul>
            </div>
          </div>
        </div>
        <div class="header_search">
          <div class="wrapper">
            <input type="text" name="keyword" /><a href="javascript:;"></a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
// import {mapState} from 'vuex'
export default {
  name: 'nav-header',
  data() {
    return {
      username: 'jack',
      phoneList: [],
    }
  },
  filters:{
    currency(val){
      if(!val) return '0.00';
      return `￥${val.toFixed(2)}元`;
      // '￥'+val.toFixed(2)+'元'
    }
  },
  mounted() {
    this.getProductList();
  },
  methods: {
    login(){
       this.$router.push('/login');
    },
     getProductList(){
        this.axios.get('/products',{
          params:{
            categoryId:'100012',
            pageSize:6
          }
        }).then((res)=>{
          this.phoneList = res.list;
        })
    },
    goToCart(){
      this.$router.push('/cart');
    }
  },
}
</script>
<style lang="scss">
@import './../assets/scss/base.scss';
@import './../assets/scss/mixin.scss';
@import './../assets/scss/config.scss';
.header {
  .nav_topbar {
    height: 39px;
    line-height: 39px;
    background-color: #333;
    color: #b0b0b0;
    .container {
      width: 1226px;
      margin-right: auto;
      margin-left: auto;
      @include flex();
      a {
        display: inline-block;
        font-size: 12px;
        color: #b0b0b0;
        margin-right: 17px;
      }
      .my_cart {
        width: 110px;
        background-color: $colorA;
        text-align: center;
        color: aliceblue;
        .icon_cart {
          @include bgImg(16px, 12px, '/imgs/icon-cart-checked.png');
          display: inline-block;
          margin-right: 6px;
        }
      }
    }
  }
  .nav_header {
    .container {
      position: relative;
      width: 1226px;
      margin-right: auto;
      margin-left: auto;
      height: 112px;
      @include flex();
      .header_logo {
        display: inline-block;
        width: 55px;
        height: 55px;
        background-color: $colorA;
        overflow: hidden;
        a {
          display: inline-block;
          width: 110px;
          height: 55px;
          &:before {
            content: '';
            display: inline-block;
            @include bgImg(55px, 55px, '/imgs/mi-logo.png');
            transition: margin 0.5s;
          }
          &:after {
            content: '';
            display: inline-block;
            @include bgImg(55px, 55px, '/imgs/mi-home.png');
          }
          &:hover:before {
            margin-left: -55px;
            transition: margin 0.5s;
          }
        }
      }
      .header_menu {
        display: inline-block;
        // padding-left: 209px;
        width: 643px;
        .items_menu {
          display: inline-block;
          color: #333;
          font-weight: bold;
          font-size: 16px;
          line-height: 55px;
          text-align: center;
          margin-right: 20px;
          span {
            display: inline-block;
            cursor: pointer;
          }
          &:hover {
            color: $colorA;
            .children {
              height: 220px;
              opacity: 1;
            }
          }
          .children {
            position: absolute;
            top: 112px;
            left: 0;
            width: 1226px;
            border-top: 1px solid $colorH;
            overflow: hidden;
            box-shadow: 0px 7px 6px 0px rgba(0, 0, 0, 0.11);
            height: 0;
            opacity: 0;
            z-index: 10;
            transition: all 0.5s;
            background-color: #fff;
            .product {
              position: relative;
              float: left;
              width: 16.6%;
              height: 220px;
              font-size: 12px;
              line-height: 12px;
              text-align: center;
              a {
                display: inline-block;
              }
              img {
                height: 111px;
                width: auto;
                margin-top: 26px;
              }
              .pro_img {
                height: 137px;
              }
              .pro_name {
                font-weight: bold;
                margin-top: 19px;
                margin-bottom: 8px;
                color: $colorB;
              }
              .pro_price {
                color: $colorA;
              }
              &:before {
                content: '';
                position: absolute;
                top: 28px;
                right: 0;
                border-right: 1px solid $colorF;
                height: 100px;
                width: 1px;
              }
              &:last-child:before {
                display: none;
              }
            }
          }
        }
      }
      .header_search {
        width: 319px;
        .wrapper {
          height: 50px;
          border: 1px solid #e0e0e0;
          display: flex;
          align-items: center;
          input {
            border: none;
            border-right: 1px solid #e0e0e0;
            width: 264px;
            height: 50px;
            padding-left: 14px;
            box-sizing: border-box;
          }
          a {
            display: inline-block;
            @include bgImg(18px, 18px, '/imgs/icon-search.png');
            margin-left: 17px;
          }
        }
      }
    }
  }
}
</style>
