<template>
    <slot></slot>
</template>

<script>
export default {
    name: 'FormValidation',
    props: {

    },
    data() {
        return
    },
    methods: {
        isValid() {
                if(1) {
                    alert("buba")
                } else {
                    alert("huba")
                }
            }
    }
  
}
</script>

<style lang="scss">
    .errors {
        border: red
    }
</style>