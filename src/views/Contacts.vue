<template>
    <div class="counter">
        counter: {{ counter }}
    </div>
    
</template>

<script>
export default {
    data () {
        return {
            counter: 0,
        }
    },
    mounted() {
        setInterval(()=> {
            this.counter++
        }, 1000)
    }
}
</script>

