<template>
  <transition name="modal">
    <div class="modal__mask" >
      <div class="modal__wrapper">
        <div class="modal__container">
          <div class="modal__header">
              Header
          </div>

          <div class="modal__body">
              Body
          </div>

          <div class="modal__footer">
              Footer
          </div>
          <button @click="close"> ok </button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'ModalItem',
    methods: {
      close() {
        this.$emit('close');
      },
    },
  };
</script>

<style lang="scss" scoped>
  .modal {

    &__mask {
      position: fixed;
      z-index: 9998;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      display: table;
      transition: opacity 1s ease;
    }

    &__wrapper {
      display: table-cell;
      vertical-align: middle;
    }


    &__container {
      width: 1000px;
      margin: 0px auto;
      padding: 20px 30px;
      background-color: #fff;
      border-radius: 2px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
      transition: all 0.3s ease;
    }

    &__header {
      margin: 20px 0;
      color: black;
    }

    &__body {
      margin: 20px 0;
      color: black;
    }

    &__footer {
      margin: 20px 0;
      color: black;
    }

    &-enter {
      opacity: 0;
    }

    &-leave-active {
      opacity: 0;
    }
  }
</style>