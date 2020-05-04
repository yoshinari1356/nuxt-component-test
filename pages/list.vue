<template>
  <div class="">
    <h1>list page</h1>
    <h2>item data()の中に直で書いているケース</h2>
    <v-layout v-for="(item, i) in items" :key="i">
      <v-flex>
        <listItem :item="item"></listItem>
      </v-flex>
    </v-layout>
    <h2>item2 asyncDataで先に読み込む</h2>
    <v-layout v-for="(item, i) in items2" :key="i">
      <v-flex>
        <listItem :item="item"></listItem>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import $axios from 'axios'
import listItem from '~/components/listItem'
export default {
  components: {
    listItem
  },
  asyncData() {
    return $axios.get(`http://localhost:3004/users`).then((res) => {
      const items2 = res.data
      return { items2 }
    })
  },
  data() {
    return { items: [{ id: 1 }, { id: 2 }, { id: 3 }, { id: 4 }, { id: 5 }] }
  }
}
</script>

<style></style>
