<template>
  <transition name="slide">
    <div class="modal" v-show="showModal">
      <div class="mask"></div>

      <div class="modal_dialog">
        <div class="modal_header">
          <span>{{title}}</span>
          <a href="javascript:;" class="icon_close" v-on:click="$emit('cancel')"></a>
        </div>
        <div class="modal_body">
          <slot name="body"></slot>
        </div>
        <div class="modal_footer">
           <a href="javascript:;" class="btn" v-if="btnType==1" v-on:click="$emit('submit')">{{sureText}}</a>
          <a href="javascript:;" class="btn" v-if="btnType==2" v-on:click="$emit('cancel')">{{cancelText}}</a>
          <div class="btn_group"  v-if="btnType==3">
            <a href="javascript:;" class="btn" v-on:click="$emit('submit')">{{sureText}}</a>
            <a href="javascript:;" class="btn" v-on:click="$emit('cancel')">{{cancelText}}</a>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>
<script>
export default {
  name: 'modal',
  props: {
    modalType: {
      type: String,
      default: 'form',
    },
    title: String,
    btnType: String,
    sureText: {
      type: String,
      default: '确定',
    },
    cancelText: {
      type: String,
      default: '取消',
    },
    showModal: Boolean,
  },
}
</script>
<style lang="scss">
@import './../assets/scss/config.scss';
@import './../assets/scss/mixin.scss';
@import './../assets/scss/modal.scss';
</style>
