<template>
    <div class="items-list">
        <table class="items-list__table">
            <tr class="items-list__table-row items-list__table-head">
                <th class="name">Item Name</th>
                <th class="qty">Qty</th>
                <th class="price">Price</th>
                <th class="total">Total</th>
            </tr>
            <list-row></list-row>
        </table>

        <div class="items-list__button">
            <img src="@/assets/icon-plus.svg" />
            Add New Item
        </div>
    </div>
</template>
<script>
import ListRow from './listRow.vue'
export default {
    name: 'itemList',
    components: {
        ListRow
    },
    data() {
        return  {
        }
    }
}
</script>
<style lang="scss">
.items-list {
    width: 100%;
    margin: 20px 0 20px;

    &__table {
        width: 100%;

        &-row {
            display: flex;
            gap: 16px;

            th,td {
                text-align: left;
            }
            .name {
                flex-basis: 50%;
            }
            .qty {
                flex-basis: 10%;
            }
            .price {
                flex-basis: 20%;
            }
            .total {
                flex-basis: 20%;
            }
        }
    }

    &__button {
        cursor: pointer;
        width: 100%;
        background-color: #1e2139;
        border-radius: 30px;
        margin: 16px 0;
        padding: 18px;
        text-align: center;
    }
}
</style>