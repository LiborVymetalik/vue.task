<template>
  <ul>
    <li v-for="(item, index) in jsonData"
      :key="index"
    >
      <div class="card">
        <div class="card-content">
          <list-person-icon />
          <h3>{{ item.dataPublic }}</h3>
          <p>
            {{ item.about.substring(0,65) + "..."}}
          </p>
        </div>
        <div class="card-line"></div>
      </div>
    </li>
  </ul>
</template>

<script>
import ListPersonIcon from '@/components/ListPersonIcon.vue'
import jsonData from '@/data/data.json'

export default {
  name: 'ListPerson',
  components: {
    ListPersonIcon
  },
  data () {
    return {
      jsonData: jsonData
    }
  },
  created () {
    this.jsonData.forEach(item => {
      item.dateParse = Date.parse(item.registered)
      item.dataPublic = item.registered.split(',')[1].trim().split(' ').reverse().join(' ')
    })
    this.jsonData = this.jsonData.sort((a, b) => a.dateParse - b.dateParse)
  }
}
</script>

<style lang="scss" scoped>
@use '@/scss/_variables' as *;

.card {
  align-items: center;
  display: flex;

  @media (max-width: 767px) {
    margin-bottom: 3rem;
  }

  &-content {
    padding: 0 2.5rem;

    @media (max-width: 767px) {
      width: 100%;
    }
  }

  &-line {
    align-items: center;
    background-color: $color-primary;
    display: flex;
    flex-shrink: 0;
    height: 4px;
    justify-content: space-between;
    width: 100px;
    z-index: 9;

    @media (max-width: 767px) {
      display: none;
    }

    &::after,
    &::before {
      background: $color-primary;
      border: 4px solid $color-primary;
      border-radius: 50%;
      content: '';
      height: 12px;
      transform: translate(-10px, 0px);
      width: 12px;
    }

    &::after {
      background: $color-secondary;
      transform: translate(10px, 0px);
    }
  }
}

ul {
    padding: 5rem 0;
}

li {
  list-style-type: none;
  max-width: 50%;
  text-align: center;

  @media (max-width: 767px) {
    max-width: 100%;
  }

  &:nth-child(even) {
    margin: 0 0 0 auto;

    .card {
      flex-direction: row-reverse;
    }

    .card-line {
      &::after {
        background: $color-primary;
        border-color: $color-primary;
      }

      &::before {
        background: $color-secondary;
        border: 4px solid $color-primary;
      }
    }
  }
}
</style>
