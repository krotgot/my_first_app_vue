<template>
    <div class="items-list">
        <table class="items-list__table">
            <tr class="items-list__table-row items-list__table-head">
                <th class="name">Item Name</th>
                <th class="qty">Qty</th>
                <th class="price">Price</th>
                <th class="total">Total</th>
            </tr>
            <tr class="items-list__table-row"
                v-for="(item, index) in itemsList"
                :key="index"
            >
                <td class="name">
                    <input type="text" v-model="item.name">
                </td>
                <td class="qty">
                    <input type="text" v-model="item.qty">
                </td>
                <td class="price">
                    <input type="text" v-model="item.price">
                </td>
                <td class="total">
                    {{item.total = item.qty * item.price}} &#8381;
                </td>
                <div class="items-list__button--delete"
                @click="deleteItem"
                >
                    &#10006;
                </div>
            </tr>
        </table>

        <div class="items-list__button"
            @click="addNewItem"
        >
            <img src="@/assets/icon-plus.svg" />
            Add New Item
        </div>
    </div>
</template>
<script>

export default {
    name: 'itemList',
    data() {
        return  {
            itemsList: [],

        }
    },
    methods: {
        addNewItem() {
            this.itemsList.push({
                name: "",
                qty: "",
                price: "",
                total: ""
            })
        },
        deleteItem(index) {
            this.itemsList.splice(index, 1)
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
            margin: 15px 0;

            td {
                display: flex;
                flex-direction: column;
                justify-content: center;
                input {
                
                    width: 100%;
                    color: #fff;
                    background-color: #1e2139;
                    border: none;
                    border-radius: 4px;
                    padding: 12px 4px;

                    &:focus,
                    &:focus-visible {
                        outline: none;
                    }
                }
            }

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

        &--delete {
            cursor: pointer;
            display: flex;
            align-items: center;
        }
    }
}
</style>