<!-- eslint-disable no-tabs -->
<template>
  <div class="loader " v-show="photosRequest.pending">
		<ProgressSpinner />
	</div>
	<div class="loader " v-show="photosRequest.error">
		<h1>Error! Try again....</h1>
	</div>
    <div ref="catalog" class="scrollContainer">
		<PhotosList
    class="grid"
    :photos="photos"
    :isHomePage="category ? false : true"
    @vote="addVote2($event)"></PhotosList>
	</div>
</template>
<script>
import { mapGetters, mapActions, mapState } from 'vuex'
import ProgressSpinner from 'primevue/progressspinner'
import PhotosList from '../shared/PhotosList.vue'
export default {
  name: 'PhotosCatalog',
  data () {
    return {
      currentPage: 1
    }
  },
  props: {
    category: {
      type: String
    }
  },
  computed: {
    ...mapGetters({ photos: 'Photos/allPhotos' }),
    ...mapState('Photos', ['photosRequest'])
  },
  methods: {
    ...mapActions('Photos', ['fetchPhotos', 'fetchCategoryPhotos', 'addVote']),
    addVote2 (id) {
      this.addVote(id)
    },
    loadPhotos () {
      this.currentPage++
      if (!this.category) this.fetchPhotos(this.currentPage)
      else {
        this.fetchCategoryPhotos({
          category: this.category,
          page: this.currentPage
        })
      }
    },
    handleScroll () {
      const elem = this.$refs.catalog
      const bottomOfWindow =
        Math.ceil(elem.scrollTop) >= elem.scrollHeight - elem.offsetHeight
      if (bottomOfWindow) this.loadPhotos()
    },
    prepareScroll () {
      this.$refs.catalog.addEventListener('scroll', () => {
        this.handleScroll()
      })
    }
  },
  created () {
    if (!this.category) this.fetchPhotos(1)
    else this.fetchCategoryPhotos({ category: this.category, page: 1 })
  },
  mounted () {
    this.prepareScroll()
  },
  components: { PhotosList, ProgressSpinner }
}
</script>

<style scoped lang="scss">
.scrollContainer {
  max-height: 1200px;
  overflow-y: auto;
  overflow-x: hidden;
  padding: 15px;
  margin-bottom: 1rem;
}
.loader{
  position:absolute;
  background-color: aliceblue;
  height: 100%;
  width: 100%;
  z-index: 100;
  opacity: 0.9;
}
</style>
