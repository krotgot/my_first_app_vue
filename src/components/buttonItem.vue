<template>
        <div class="button-item"
        :class="className"
        >
        </div>
</template>

<script>


export default {
    name: "button-item",
    props: {
        cancel: {
            type: String,
            default: 'Cancel'
            
        },
        draft: {
            type: String,
            default: 'Save Draft'
        },
        create: {
            type: String,
            default: 'Create invoice'
        },
        
    },
    data() {
        return {
        }
    },
    computed: {
        className() {
            return {

                'button-item__cancel' : this.cancel,
                'button-item__draft' : this.draft,
                'button-item__create' : this.create,
            }
        }
    },
    methods: {
        },
    
        
    }
</script>

<style lang="scss">

    .button-item {
        display: flex;
        justify-content: space-between;
        background-color: #57d513;
        

    &__cancel {
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #e60d0d;
        border-radius: 40px;
        color: black;
        
        width: 100px;
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