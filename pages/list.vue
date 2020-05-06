<template>
  <div class="">
    <h1>list page</h1>
    <h2>item data()の中に直で書いているケース</h2>
    <v-layout v-for="(item, i) in items" :key="`1-${i}`">
      <v-flex>
        <listItem :item="item"></listItem>
      </v-flex>
    </v-layout>
    <h2>item2 asyncDataで先に読み込む</h2>
    <v-layout v-for="(item, i) in items2" :key="`2-${i}`">
      <v-flex>
        <listItem :item="item"></listItem>
      </v-flex>
    </v-layout>
    <h2>item3 fetchで描画直前に読み込み</h2>
    <v-layout v-for="(item, i) in items3" :key="`3-${i}`">
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
  fetch() {
    // `fetch` メソッドはページの描画前にストアを満たすために使用されます
    return $axios.get(`http://localhost:3004/users`).then((res) => {
      console.log('fetch', res)
      this.items3 = res.data
    })
  },
  asyncData() {
    return $axios.get(`http://localhost:3004/users`).then((res) => {
      const items2 = res.data
      return { items2 }
    })
  },
  data() {
    return {
      items: [{ id: 1 }, { id: 2 }, { id: 3 }, { id: 4 }, { id: 5 }],
      beforeCreate() {
        console.log('beforeCreate')
      },
      created() {
        console.log('created')
      },
      beforeMount() {
        console.log('beforeMount')
      },
      mounted() {
        console.log('mounted')
      },
      beforeDestroy() {
        console.log('beforeDestroy')
      },
      destroyed() {
        console.log('destroyed')
      },
      beforeUpdate() {
        console.log('beforeUpdate')
      },
      updated() {
        console.log('updated')
      }
    }
  },
  head() {
    // このページ向けにメタタグを設定します
    return {
      meta: [
        { charset: 'utf-8' },
        { name: 'viewport', content: 'width=device-width, initial-scale=1' }
      ],
      link: [
        {
          rel: 'stylesheet',
          href: 'https://fonts.googleapis.com/css?family=Roboto'
        }
      ]
    }
  }
}
</script>

<style></style>
