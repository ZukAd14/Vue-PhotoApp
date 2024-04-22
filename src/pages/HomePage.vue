<template>
  <div class="page">
    <page-title>
      <template v-slot>Photos</template>
    </page-title>
    <photos-catalog />
  </div>
</template>

<script>
import PageTitle from '../components/layout/PageTitle'
import PhotosCatalog from '../components/features/PhotosCatalog'

export default {

  name: 'HomePage',

  components: {
    PageTitle,
    PhotosCatalog
  }
}
</script>
