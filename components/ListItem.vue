<template>
  <div class="listItem">{{ item.id }} : listitem</div>
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
