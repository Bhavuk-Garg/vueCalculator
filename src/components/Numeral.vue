<template>
        <v-btn @click="$emit('clicked',numeralValue)" width="90%" tile>{{numeralValue}}</v-btn>
</template>

<script>
export default {
  props: ['numeralValue']
}
</script>

<style>

</style>