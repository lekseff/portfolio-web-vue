<template>
  <v-btn class="mx-1 my-0" :value="filter.value">
    <v-icon left>mdi-{{ filter.icon }}</v-icon>
    <span>{{ filter.title }}</span>
  </v-btn>
</template>

<script>
export default {
  name: 'AppFiltersButton',
  props: ['filter'],
};
</script>

<style lang="scss" scoped></style>
