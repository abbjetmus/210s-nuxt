<template>
  <div class="flex flex-wrap justify-center">
    <div @click="goToDish(dish.id)" class="w-80 m-4" v-for="dish in dishes" :key="dish.id">
      <DishListItem :item="dish"></DishListItem>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({$content}) {
    let dishes = await $content('dishes').without(['body']).fetch()
    return {
      dishes
    }
  },
  methods: {
    goToDish(id) {
      this.$router.push('/dish-details/'+id)
    }
  }
}
</script>
