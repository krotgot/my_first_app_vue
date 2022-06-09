<template>
    <div class="button-item" @click="klak">
        <div class="button-item__cancel" >
            Cancel
        </div>
        <div class="button-item__draft">
            Save Draft
        </div>
        <div class="button-item__create">
            Create invoice
        </div>
    </div>
</template>

<script>
export default {
    name: "button-item",
    props: {},
    data () {
        return {}
    },
    methods: {
        klak () {
            this.$emit ("klak")
        }
    },

    computed: {}
}
</script>

<style lang="scss">

.button-item {
    display: flex;
    justify-content: space-around;
    background-color: #141625;
    color: white;

    &__cancel {
        display: flex;
        align-items: center;
        background-color: #e60d0d;
        border-radius: 40px;
        padding: 8px 10px;
        cursor: pointer;
    }
    &__draft {
        display: flex;
        align-items: center;
        background-color: gray;
        border-radius: 40px;
        padding: 8px 10px;
        cursor: pointer;
    }

    &__create {
        display: flex;
        align-items: center;
        background-color: #7c5dfa;
        border-radius: 40px;
        padding: 8px 10px;
        cursor: pointer;
    }
    
}

</style>