<template>
  <div class="modal" v-show="showModal">
    <div class="modal_dialog">
      <div class="modal_header">
        <span>标题</span>
        <a href="javascript:;" class="icon_close"></a>
      </div>
      <div class="modal_body">
        <slot name="body"></slot>
      </div>
      <div class="modal_footer">
        <a href="javascript:;" class="btn">确定</a>
        <a href="javascript:;" class="btn">取消</a>
      </div>
    </div>
  </div>
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
      default: '取消'
    },
    showModal: Boolean
  },
}
</script>
<style lang="scss">
@import './../assets/scss/config.scss';
@import './../assets/scss/mixin.scss';
@import './../assets/scss/modal.scss';
</style>
