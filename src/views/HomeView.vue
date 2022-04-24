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
      <div class="body__list-items">
        <div>№98E285</div>
        <div>Nov 29, 2021</div>
        <div>Sergey Tverezovskii</div>
        <div>
          <b>$47</b>
        </div>
        <div class="body__list-button">
          <button>Draft</button>
        </div>
        <div>
          <img src="@/assets/icon-arrow-down.svg" />
        </div>
      </div>
      <div class="body__list-items">
        <div>№C2310B</div>
        <div>Oct 30, 2021</div>
        <div>Krelectro</div>
        <div>
          <b>$70</b>
        </div>
        <div class="body__list-button">
          <button>Paid</button>
        </div>
        <div>
          <img src="@/assets/icon-arrow-down.svg" />
        </div>
      </div>
      <div class="body__list-items">
        <div>№8FF75D</div>
        <div>Oct 30, 2021</div>
        <div>Yconsultant</div>
        <div>
          <b>$35</b>
        </div>
        <div class="body__list-button">
          <button>Pending</button>
        </div>
        <div>
          <img src="@/assets/icon-arrow-down.svg" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'HomeView',
    data() {
      return {
        filterMenu: false
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

        &-inner {
          display: flex;
          justify-content: center;
          align-items: center;
          border-radius: 50%;
          padding: 8px;
          margin-right: 8px;
          background-color: #fff;
          cursor: pointer;

          img {
            width: 10px;
            height: 10px;
          }
        }
      }
    }
  }

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

        img {
          transform: rotate(-90deg);
        }
      }
    }
  }
</style>