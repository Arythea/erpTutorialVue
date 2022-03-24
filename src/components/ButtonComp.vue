<template>
  <button @click="move">{{ labelProp }}</button>
</template>

<script>
export default {
  name: 'ButtonComp',
  props: ['labelProp'],
  methods: {
    move() {
      this.$emit('moveScene',this.labelProp)
    }
  }
}
</script>

<style scoped>

</style>