<template>
  <div class="">
    <v-layout v-for="(item, i) in items" :key="i">
      <v-flex>
        test
        <listItem :item="item"></listItem>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import listItem from '~/components/listItem'
export default {
  components: {
    listItem
  },
  data() {
    return { items: [{ id: 1 }, { id: 2 }, { id: 3 }, { id: 4 }, { id: 5 }] }
  }
}
</script>

<style></style>
