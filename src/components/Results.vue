<template>
    <p>Your Reaction Time: {{ score }} ms</p>
    <p class="rank"> {{ rank }} </p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 300) {
            this.rank = "Hollly shit! GOD fingers"
        } else if (this.score < 500) {
            this.rank = "Rapid flexes!"
        } else {
            this.rank = "Good try..."
        }
    },

}
</script>

<style>
    .rank{
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>