<template>
  <transition tag="div" name="page" appear>
    <div class="home" >
      <div class="middle-line"></div>
      <list-person />
    </div>
  </transition>
</template>

<script>
import ListPerson from '@/components/ListPerson.vue'

export default {
  name: 'Home',
  components: {
    ListPerson
  }
}
</script>

<style lang="scss">
@use '@/scss/_variables' as *;

* {
    box-sizing: border-box;
}

html {
    font-family: sans-serif;
    font-size: 16px;
}

h3 {
    color: $color-primary;
    margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

.home {
  margin: 3rem auto;
  max-width: 800px;
  position: relative;
}

.middle-line {
  align-items: center;
  background-color: $color-primary;
  display: flex;
  flex-direction: column;
  height: 100%;
  justify-content: space-between;
  left: 0;
  margin: auto;
  position: absolute;
  right: 0;
  width: 4px;

  @media (max-width: 767px) {
      display: none;
  }

  &::before,
  &::after {
    content: '';
    height: 20px;
    width: 20px;
    background: $color-primary;
    display: block;
    border-radius: 50%;
    transform: translate(0px, -10px);
  }

  &::after {
    transform: translate(0px, 10px);
  }
}

.page-enter-from {
  opacity: 0;
  transform: scale(1.03);
}

.page-enter-to {
  opacity: 1;
  transform: scale(1);
}

.page-enter-active {
  transition: all 0.5s;
}
</style>
