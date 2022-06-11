<template>
  <div class="modal" >
    <div class="modal__wrapper">
      <div class="modal__container">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'ModalItem',
    data() {
      return {
        text: ''
      }
    }
  };
</script>

<style lang="scss" scoped>
  .close {
    color: white;
    position: absolute;
    right: 20px;
    top: 10px;
    cursor: pointer;
  }
  .modal {
    position: fixed;
    z-index: 9998;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: table;
    transition: opacity 1s ease;

    &__wrapper {
      display: table-cell;
      vertical-align: middle;
    }

    &__container {
      position: relative;
      width: 1000px;
      height: 80vh;
      overflow-y: auto;
      margin: 0px auto;
      padding: 20px 30px;
      background-color: #141625;
      border-radius: 2px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
      transition: all 0.3s ease;
      color: #000;
    }
  }
</style>