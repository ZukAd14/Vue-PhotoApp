<template>
<header class="header ml-5 mt-2 mb-2 flex justify-content-between border-bottom">
<p><a href="/">Photos App </a>|Share your photo</p>
<Button
type="button"
size="large"
label="Submit"
icon="pi pi-plus"
rounded
@click="$router.push('/add-photo')" />
</header>
<CategoriesList class="mt-4" />
</template>
<script>
import Button from 'primevue/button'
import CategoriesList from '../features/CategoriesList.vue'
export default {
  name: 'theHeader',
  components: {
    Button,
    CategoriesList
  }
}
</script>
<style lang="scss">

a{
    text-decoration: none;
    font-size: 1.5rem;
    font-weight: bolder;
}
</style>
<style scoped>

.header > .p-button {

  border-radius: 1.5rem;
  padding: 0.5rem 1rem;
}

.header > .p-button.p-button-outlined {
  border: 1px solid #007bff;
  color: #007bff;
}
.header > .p-button.p-button-outlined:hover {
  background-color: #007bff;
  color: #fff;
}

.logo {
  font-weight: bold;
  font-size: 1.5rem;
}
.border-bottom {
  border-bottom: 1px solid #ccc;
}
.mt-4 {
  margin-top: 1.5rem;
}
</style>
