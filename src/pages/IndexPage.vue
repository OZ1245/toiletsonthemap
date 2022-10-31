<template>
  <q-page class="page flex flex-center">
    <osm-map></osm-map>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import OsmMap from 'components/OsmMap.vue'

export default defineComponent({
  name: 'IndexPage',

  components: {
    'osm-map': OsmMap
  }
})
</script>

<style lang="scss" scoped>
.page {
  width: 100%;
}
</style>
