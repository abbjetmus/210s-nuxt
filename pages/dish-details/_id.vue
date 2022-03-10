<template>
<div class="w-1/2 mx-auto">
    <img :src="dish.image" />
    <h1 class="text-5xl mb-8">{{dish.title}}</h1>
    <p class="mb-8">{{dish.description}}</p>
    <nuxt-content :document="dish"></nuxt-content>
</div>
</template>
<script>
export default {
    async asyncData({$content, params}) {
        
        let dish = await $content('dishes/dish'+params.id).fetch()
        console.log(dish)

        return {
            dish
        }
    },
}
</script>