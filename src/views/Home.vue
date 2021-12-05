<template>
 <h1>Reaction Timer</h1>
 <button @click="start" :disabled="isPlaying">Play</button>
 <TheBlock  v-if="isPlaying" :delay="delay" @end="endGame"/>
 <TheResults v-if="showResults" :score="score" />
</template>

<script>
// @ is an alias to /src
import TheBlock from '@/components/TheBlock.vue'
import TheResults from '@/components/TheResults.vue'

export default {
  name: 'Home',
  components: {
    TheBlock,
    TheResults
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000,
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true

    }
  }
}
</script>

<style scoped>
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}

</style>
