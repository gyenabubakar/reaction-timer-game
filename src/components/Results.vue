<template>
  <p>
      💎&nbsp;Your Reaction Time: {{ score }} ms
  </p>

  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    name: 'Results',
    props: ['score'],
    
    data() {
        return {
            rank: null
        }
    },

    mounted() {
        if (this.score < 250) {
            this.rank = '⚡⚡ Ninja Fingers 🖐🤞'
        } else if (this.score < 450) {
            this.rank = '💪 Rapid Reflexes 😁'
        } else {
            this.rank = '🐌 Snail pace 🛣'
        }
    }
}
</script>

<style scoped>
p {
    text-align: center;
}

p.rank {
    color: rgb(11, 3, 34);
    font-size: 1.2rem;
    font-weight: bolder;
}
</style>