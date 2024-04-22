<template>
  <div class="image-container"
       @mouseover="isHovered = true"
       @mouseleave="isHovered = false">
    <div
    class="colored"
    :class="{ 'show': isHovered }"
    @click="$emit('vote')"
    @mouseleave="mouseOver"></div>
    <img :src="imageSrc" class="image" @mouseenter="mouseOver" />
    <i class="pi pi-star star-icon" v-show="isHovered"></i>
  </div>
</template>

<script>
import { imagesUrl } from '@/config'

export default {
  name: 'PhotosList',
  data () {
    return {
      isHovered: false
    }
  },
  props: {
    src: {
      type: String,
      required: true
    }
  },
  computed: {
    imageSrc () {
      return `${imagesUrl}/${this.src}`
    }
  }
}
</script>

<style lang="scss">
.image-container {
  position: relative;
}

.image {
  height: 350px;
  width: 220px;
  object-fit: cover;
}

.colored {
  height: 100%;
  width: 100%;
  background-color: rgba(155, 89, 182, 0.5);
  position: absolute;
  z-index: 100;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.colored.show {
  opacity: 1;
}

.star-icon {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 3rem;
  opacity: 0.8;
}

.star-icon:hover {
  opacity: 1;
}
</style>
