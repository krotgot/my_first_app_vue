<template>
    <div class="body__list-items">
        <div class="body__list-block body__list-block--left">
            <div class="body__list-item">{{item.number}}</div>
            <div class="body__list-item">{{item.date}}</div>
            <div class="body__list-item">{{item.name}}</div>
        </div>
        <div class="body__list-block">
            <div>
                <span class="typography_span">{{item.check}}</span>
            </div>
            <div class="button__default"
              :class="buildClass"
            >{{status}}</div>
            <div>
                <img src="@/assets/icon-arrow-down.svg" />
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'InvoiceItem',
        props: {
          item: Object,
        },
        data() {
          return { 
            status: ""
          }
        },
        computed: {
          buildClass() {
            this.status = this.item.status ? this.item.status : "No status"
            return `button__default--${this.item.status?.toLowerCase()}`

            // 34-35 строка вместо всего этого!!!
            // switch (this.item.status) {
            //   case "Draft":
            //     this.status = this.item.status
            //     return "button__default--draft"
            //   case "Pending":
            //     this.status = this.item.status
            //     return "button__default--pending"
            //   case "Paid":
            //     this.status = this.item.status
            //     return "button__default--paid"
            //   case "Cancelled":
            //     this.status = this.item.status
            //     return "button__default--cancelled"
            //   default: 
            //     return ""
            // }   
          }
        }
    }
</script>
<style lang="scss" scoped>
  .body {

    &__list {
    
      &-items {
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #1e2139;
        box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        height: 80px;
        border-radius: 20px;
        padding: 20px;
        margin: 20px;
        gap: 40px;

        img {
          transform: rotate(-90deg);
          cursor: pointer;
        }
      }

      &-item {
        flex: 1;
        // white-space: nowrap;
        font-size: 14px;
      }

      &-block {
        display: flex;
        justify-content: space-between;
        flex-basis: 40%;
        align-items: center;

        &--left {
          flex-basis: 60%;
        }
      }
    }
  .button__default {
        height: 40px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 20px;
        padding: 0 16px;
        opacity: .6;
        min-width: 124px;
        background-color: rgba(223, 227, 250, 0.1);
        color: #dfe3fa;

      &:before {
        content: 	'\2022';
        font-size: 40px;
        padding-right: 10px;
      }
      
      &--draft {
        background-color: rgba(130, 8, 114, 0.4);
        color: #c542d7;
      }

      &--paid {
        background-color: rgba(193, 174, 28, 0.1);
        color: #be8903;
      }
      &--pending {
        background-color: rgba(51, 214, 160, .1);
        color: #10df32;
      }
      &--cancelled {
        background-color: rgba(43, 18, 206, 0.776);
        color: #e6f911e4;
      }
     }
  }
</style>