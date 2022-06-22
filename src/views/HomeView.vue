<template>
  <div class="home container">
    <!-- Header -->
    <div class="home__header">
      <div class="home__header-title">
        <h1>Invoices</h1>
        <div>There are 3 total Invoices</div>
      </div>
      <div class="home__header-controls">
        <div class="home__header-filter" @click="toggleFilterMenu">
          Filter by
          <div class="current-status__default" :class="`current-status__default--${currentStatus}`"> {{currentStatus}}</div>
          <img src="@/assets/icon-arrow-down.svg" />
          <ul class="home__header-list" v-show="filterMenu">
            <li v-for="(item, index) in statusList" :key="index" @click="changeStatus(item)"
              class="home__header-list-item">{{ item }}</li>
          </ul>
        </div>
        <div class="home__header-button" @click="showModal">
          <div class="home__header-button-inner">
            <img src="@/assets/icon-plus.svg" />
          </div>
          <span>New Invoice</span>
        </div>
        <modal-item v-if="isModalVisible"> 
          <add-invoice @closeModal="isModalVisible = false"></add-invoice>
          
        </modal-item>
      </div>
    </div>
  </div>
  <div class="body container">
    <div class="body__list">
      <div v-for="(i, index) in invoiceItems" :key="index">
        <invoice-item :item="i"
          v-if="i.status === currentStatus || currentStatus === 'all' || (currentStatus === 'No status' && !i.status)">
        </invoice-item>
      </div>
    </div>
  </div>
</template>

<script>
  import InvoiceItem from '@/components/invoiceItem.vue'
  import ModalItem from '@/components/modalItem.vue'
  import AddInvoice from '@/components/addInvoice.vue'
  import ButtonItem from '@/components/buttonItem.vue'
  export default {
    name: 'HomeView',
    components: {
      InvoiceItem,
      ModalItem,
      AddInvoice,
      ButtonItem
    },
    data() {
      return {
        currentStatus: 'all',
        filterMenu: false,
        isModalVisible: false,
        invoiceItems: [{
            number: '№98E285',
            date: 'Nov 29, 2021',
            name: 'Sergey Tvkii',
            check: '$47',
            status: 'pending'
          },
          {
            number: '№98E2йцвйцв85',
            date: 'Nov 29, 2019',
            name: 'Sergey',
            check: '$470',
            status: 'pending'
          },
          {
            number: '№98E285',
            date: 'Nov 29, 2020',
            name: 'Sergey Tverezovskii',
            check: '$47',
            status: 'draft'
          },
          {
            number: '№98E285',
            date: 'Nov 29, 2022',
            name: 'Sergey',
            check: '$47',
            status: 'paid'
          },
          {
            number: '№98E285',
            date: 'Nov 29, 2021',
            name: 'wefwefwefewfw',
            check: '$47'
          },
          {
            number: '3456789',
            date: 'Nov 29, 2021',
            name: 'wefwefwefewfw',
            check: '$47',
            status: 'cancelled'
          },
        ]
      }
    },
    computed: {
      statusList() {
        let tmp = new Set()
        tmp.add('all')
        tmp.add('No status')
        this.invoiceItems.map(i => {
          if (i.status) {
            tmp.add(i.status)
          }
        })
        return tmp
      }
    },
    methods: {
      checkStatus(item) {
        console.log(item)
      },
      changeStatus(status) {
        this.currentStatus = status
      },
      toggleFilterMenu() {
        this.filterMenu = !this.filterMenu
      },
      showModal() {
        this.isModalVisible = true;
      },
      // closeModal() {
      //   this.isModalVisible = false;
      // },
    },
  }
</script>

<style lang="scss" scoped>

  .home {

    //& = .home
    &__header {
      display: flex;
      justify-content: space-between;

      &-controls {
        display: flex;
        align-items: center;

        >*+* {
          margin-left: 16px;
        }
      }

      &-filter {
        display: flex;
        align-items: center;
        cursor: pointer;
        position: relative;

        img {
          width: 12px;
          height: 7px;
          margin-left: 16px;
        }
      }

      &-list {
        position: absolute;
        top: 25px;
        left: 30px;
        list-style: none;
        width: 120px;
        z-index: 2;
        background-color: #1e2139;
        box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);

        li {
          font-size: 13px;
          cursor: pointer;
          padding: 10px 20px;

          &:hover {
            color: #1e2139;
            background-color: #fff;
          }
        }
      }

      &-button {
        display: flex;
        align-items: center;
        background-color: #7c5dfa;
        border-radius: 40px;
        padding: 8px 10px;
        cursor: pointer;

        &-inner {
          display: flex;
          justify-content: center;
          align-items: center;
          border-radius: 50%;
          padding: 8px;
          margin-right: 8px;
          background-color: #fff;

          img {
            width: 10px;
            height: 10px;
          }
        }
      }
    }
  }

  .current-status__default {
    margin: 10px;
    border-radius: 5px;

    &--draft {
      color: #c542d7;
    }

    &--paid {
      color: #be8903;
    }

    &--pending {
      color: #10df32;
    }

    &--cancelled {
      color: #e6f911e4;
    }
  }
</style>