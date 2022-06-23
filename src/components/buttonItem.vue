<template>
    <div class="button-item" :class="className">
        <slot></slot>
    </div>
</template>

<script>
    export default {
        name: "button-item",
        props: {
            theme: {
                type: String,
                default: "default"
            }
        },
        data() {
            return {}
        },
        computed: {
            className() {
                return `button-item__${this.theme}`
            }
        },
        methods: {},


    }
</script>

<style lang="scss">
    .button-item {

        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        border-radius: 40px;
        padding: 10px;
        margin: 10px;
        width: 150px;
        cursor: pointer;



        &__cancel {
            background-color: #e60d0d;
        }

        &__default {
            background-color: gray;
        }

        &__create {
            background-color: #7c5dfa;
        }
    }
</style>