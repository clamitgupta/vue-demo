<template>
  <div class="about">
    <ListSelected />
  </div>
</template>
<script>
// @ is an alias to /src
import ListSelected from '@/components/ListSelected.vue'

export default {
  name: 'List',
  components: {
    ListSelected
  }
}
</script>