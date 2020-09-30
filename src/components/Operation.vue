<template>
  <v-btn  :color="buttonColor" @click="$emit('clicked')" width="90%" tile>{{
    operationValue
  }}
    <slot></slot>
  </v-btn>
</template>

<script>
export default {
  props: {"operationValue": {
      required: true,
      default: ''
  }, 
  "buttonColor":{
      default: 'orange'
  }
  },
};
</script>

<style>
</style>