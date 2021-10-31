<template>
    <p class="results">
        Reaction Time: {{ score }} ms
    </p>
    <p class="rank">{{ rank }}</p>
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
        if (this.score < 100) {
            this.rank = "The Fastest Draw in the West"
        } else if (this.score < 250) {
            this.rank = "Lightning Quick"
        } else if (this.score < 400) {
            this.rank = "Rapid Reflexes"
        } else {
            this.rank = "Snail's Pace"
        }
    }
}
</script>

<style>
    .results {
        display: block;
        margin: 50px auto;
    }
    .rank {
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>