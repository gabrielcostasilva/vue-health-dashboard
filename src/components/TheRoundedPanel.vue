<template>
  <v-card
    class="mx-12 rounded-xl"
    :class="marginClass"
    :color="backgroundColour"
    :dark="dark"
    :flat="flat"
  >
    <slot></slot>
  </v-card>
</template>

<script>
export default {
  props: ['backgroundColour', 'marginClass', 'dark', 'flat']
}
</script>

<style></style>
