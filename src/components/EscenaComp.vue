<template>
  <div>
      <div v-for="(text, index) in textsProp" :key="index" :class="{active: index===currentSentenceProp}" class= "card p-2">
          {{ text }}
      </div>
  </div>
</template>

<script>
export default {
  name: 'EscenaComp',
  props: ['textsProp', 'currentSentenceProp']
}
</script>

<style scoped>
    .card {
        margin-top: 10px;
        opacity: 0.5;
    }
    .active {
        background: #bbffbb;
        opacity: 1 !important;
    }
</style>