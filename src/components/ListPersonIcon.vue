<template>
  <font-awesome-icon :icon="svgIcon[randomImage]" />
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faFlushed, faGrimace, faGrinBeamSweat, faGrinHearts, faGrinStars, faGrinWink }
  from '@fortawesome/free-solid-svg-icons'

export default {
  name: 'ListPersonIcon',
  components: {
    FontAwesomeIcon
  },
  data () {
    return {
      svgIcon: [faFlushed, faGrimace, faGrinBeamSweat, faGrinHearts, faGrinStars, faGrinWink]
    }
  },
  computed: {
    randomImage () {
      return Math.floor(Math.random() * this.svgIcon.length)
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
