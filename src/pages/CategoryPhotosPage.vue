<template>
    <div class="home">
    <div class="flex justify-content ml-5 mt-2 mb-2">
      <PageTitle>{{$route.params.category}}</PageTitle>
    </div>

        <PhotosCatalog :category="$route.params.category"></PhotosCatalog>
    </div>
</template>

<script>
import PageTitle from '../components/layout/PageTitle.vue'
import PhotosCatalog from '../components/features/PhotosCatalog.vue'
export default {
  name: 'CategoryPhotosPage',
  components: {
    PageTitle,
    PhotosCatalog
  }
}
</script>
