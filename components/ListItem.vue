<template>
  <div class="listItem">
    <h4>listitem</h4>
    {{ item.id }} : {{ item.name }}
  </div>
</template>
<script lang="ts">
export default {
  props: {
    item: Object({
      id: Number,
      name: String,
      data: Object
    })
  },
  data() {
    return {}
  }
}
</script>
<style>
.listItem {
  display: inline-block;
  border: solid 1px brack;
}
</style>
