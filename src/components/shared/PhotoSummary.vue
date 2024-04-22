<!-- eslint-disable no-tabs -->

<template>
  <div
		class="photo-summary card flex flex-row align-items-center justify-content-center p-shadow-4">
		<Card class="shadow-4 relative" style="width: 15rem">
			<template #header>
				<ImageItem
					class="clickable sized"
					@vote="$emit('vote')"
					:src="src"></ImageItem>
			</template>
			<div class="layer"></div>
			<template #title>
				<router-link
					:to="isHomePage ? 'photo/' + id : category + '/photo/' + id">
					<p class="clickable">
						{{ title }}
					</p>
				</router-link>
			</template>
			<template #subtitle>
				<router-link
					:to="isHomePage ? 'photo/' + id : category + '/photo/' + id">
					<p class="clickable">by {{ author }}</p>
				</router-link>
			</template>

			<template #content>
				<router-link
					:to="isHomePage ? 'photo/' + id : category + '/photo/' + id">
					<Tag class="clickable" severity="info" rounded>{{ category }} </Tag>
				</router-link>
				<div class="voting absolute top-0 right-0">
					<p style="font-weight: bolder">{{ votes }}</p>
					<Button
            @click="$emit('vote')"
						icon="pi pi-star"
						severity="help"
						text
						rounded
						size="large"
						aria-label="Favorite" />
				</div>
			</template>
		</Card>
	</div>
</template>
<script>
import Button from 'primevue/button'
import Tag from 'primevue/tag'
import Card from 'primevue/card'
import ImageItem from '@/components/layout/ImageItem.vue'
export default {
  name: 'PhotoSummary',
  components: { ImageItem, Card, Tag, Button },

  props: {
    isHomePage: {
      type: Boolean,
      default: false
    },
    id: {},
    src: {
      type: String
    },
    title: {
      type: String
    },
    author: {
      type: String
    },
    category: {
      type: String
    },
    votes: {
      type: Number
    }
  }
}
</script>
<style lang="scss">
.voting {
  height: 70px;
  width: 50px;
}
.photo-summary .p-card .p-card-content {
  padding-top: 0px;
  padding-bottom: 0px;
}
.clickable {
  cursor: pointer;
}

</style>
