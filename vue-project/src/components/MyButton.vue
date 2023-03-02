<template>
  <v-btn v-bind="$attrs" v-on="$listeners">
    <slot></slot>
    <slot name="append"></slot>
  </v-btn>
</template>

<script>
export default {
  name: "MyButton",
};
</script>
