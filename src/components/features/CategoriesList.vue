<template>
    <div class="flex justify-content ml-5 mt-2 mb-2">
        <Button class="mr-2" :key="index" v-for="(category, index) in categories" size="small" @click="$router.push('/category/'+category.name)"  :label="category.name" outlined rounded />

    </div>
</template>
<script>
import Button from 'primevue/button'
import { mapGetters } from 'vuex'
export default {
  name: 'CategoriesList',
  computed: mapGetters({ categories: 'allCategories' }),
  components: { Button }
}
</script>

<style scoped>

.flex > .p-button {

  border-radius: 1.5rem;
  padding: 0.5rem 1rem;
}

.flex > .p-button.p-button-outlined {
  border: 1px solid #007bff;
  color: #007bff;
}

.flex > .p-button.p-button-outlined:hover {
  background-color: #007bff;
  color: #fff;
}
</style>
