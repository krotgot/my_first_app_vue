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
          <span>Filter by status</span>
          <img src="@/assets/icon-arrow-down.svg" />
          <ul class="home__header-list" v-show="filterMenu">
            <li class="home__header-list-item">all</li>
            <li class="home__header-list-item">draft</li>
            <li class="home__header-list-item">pending</li>
            <li class="home__header-list-item">paid</li>
          </ul>
        </div>
        <div class="home__header-button" @click="message">
          <div class="home__header-button-inner">
            <img src="@/assets/icon-plus.svg" />
          </div>
          <span>New Invoice</span>
        </div>
      </div>
    </div>
  </div>
  <div class="body container">
    <div class="body__list">
      <invoice-item
        v-for="(i,index) in invoiceItems"
        :key="index"
        :item="i"

      ></invoice-item>
    </div>
  </div>
</template>

<script>
import InvoiceItem from '@/components/invoiceItem.vue'

export default {
  name: 'HomeView',
  components: {
    InvoiceItem
  },
  data() {
    return {
      filterMenu: false,
      invoiceItems: [
        {
          number: '№98E285',
          date: 'Nov 29, 2021',
          name: 'Sergey Tvkii',
          check: '$47',
          status: 'Pending'
        },
        {
          number: '№98E285',
          date: 'Nov 29, 2020',
          name: 'Sergey Tverezovskii',
          check: '$47',
          status: 'Draft'
        },
        {
          number: '№98E285',
          date: 'Nov 29, 2022',
          name: 'Sergey',
          check: '$47',
          status: 'Paid'
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
          status: 'Pending'
        },
      ]
    }
  },
  methods: {
    toggleFilterMenu() {
      this.filterMenu = !this.filterMenu
    },
    message() {
      console.log("когда мы начнем зарабатыват миллионы??");
    }
  }
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
        top: 50px;
        left: 0;
        list-style: none;
        width: 120px;
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
</style>