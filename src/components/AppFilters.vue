<template>
  <v-col cols="12" class="py-0 d-flex justify-center">
    <v-btn-toggle v-model="activeFilter" color="primary" group borderless>
      <AppFiltersButton
        v-for="filter in filters"
        :key="filter.value"
        :filter="filter"
      />
    </v-btn-toggle>
  </v-col>
</template>

<script>
import AppFiltersButton from './AppFiltersButton.vue';

export default {
  name: 'app-filter',
  props: ['filters'],
  components: { AppFiltersButton },
  data: () => ({
    activeFilter: 'all',
  }),
  watch: {
    activeFilter() {
      this.$emit('change-filter', this.activeFilter);
    },
  },
};
</script>

<style lang="scss" scoped></style>
