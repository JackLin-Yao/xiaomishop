<template>
  <div class="service">
    <div class="container">
      <ul>
        <li><span class="icon_setting"></span>预约维修服务</li>
        <li><span class="icon_7day"></span>7天无理由退货</li>
        <li><span class="icon_15day"></span>15天免费换货</li>
        <li><span class="icon_post"></span>满150元包邮</li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: 'service-bar',
}
</script>
<style lang="scss">
@import './../assets/scss/mixin.scss';
@import './../assets/scss/config.scss';
.service {
  padding: 33px 0;
  color: $colorC;
  font-size: 16px;
  li {
    display: inline-block;
    width: 24.8%;
    text-align: center;
    border-right: 1px solid $colorH;
  }
  span {
    display: inline-block;
    width: 20px;
    height: 20px;
    vertical-align: middle;
  }
  .icon_setting {
    @include bgImg(20px, 20px, '/imgs/icon-setting.png');
    margin-right: 8px;
  }
  .icon_7day {
    @include bgImg(20px, 20px, '/imgs/icon-7day.png');
    margin-right: 8px;
  }
  .icon_15day {
    @include bgImg(20px, 20px, '/imgs/icon-15day.png');
    margin-right: 8px;
  }
  .icon_post{
    @include bgImg(20px, 20px, '/imgs/icon-post.png');
    margin-right: 8px;
  }
}
</style>
