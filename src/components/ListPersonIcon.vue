<template>
  <font-awesome-icon :icon="svgIcon[randomImage()]" />
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { fadizzy, faFlushed, faGrimace, faGrinBeamSweat, faGrinHearts, faGrinStars, faGrinWink }
  from '@fortawesome/free-solid-svg-icons'

export default {
  name: 'ListPersonIcon',
  components: {
    FontAwesomeIcon
  },
  data () {
    return {
      svgIcon: [fadizzy, faFlushed, faGrimace, faGrinBeamSweat, faGrinHearts, faGrinStars, faGrinWink]
    }
  },
  methods: {
    randomImage () {
      let randomImage = Math.floor(Math.random() * this.svgIcon.length)
      if (!randomImage) {
        randomImage += 1
      }
      return randomImage
    }
  }
}
</script>

<style lang="scss" scoped>
@use '@/scss/_variables' as *;

.svg-inline--fa {
  color: $color-icon;
  height: 4.5rem;

  &.fa-w-16 {
    width: auto;
  }
}
</style>
