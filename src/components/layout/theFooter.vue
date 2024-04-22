<template>
    <footer>
      <h1 class="">
        <slot name="theFooter" />
        <div class="flex justify-content-between flex-wrap card-container purple-container">
        <p class="text-xs"> 2020 All rights reserved</p>
       <p class="text-xs flex align-items-center justify-content-center"> We have {{ categoriesAmount }} categories</p>
      </div>
      </h1>
  </footer>
  </template>
<script>
import { mapGetters } from 'vuex'
export default {
  name: 'theFooter',
  computed: {
    ...mapGetters(['categoriesAmount'])
  }
}
</script>
  <style>

  </style>
