<template>
  <div>
    <h1>Articles</h1>
    <div v-for="article in articles" :key="article.id" class="article">
      <div class="item gap-4">
        <VImage :image="article.thumbnail" v-if="article.thumbnail" />
        <div>
          <h2>{{ article.title }}</h2>
          <p>{{ article.description }}</p>
          <p>{{ article.price }}</p>
        </div>
      </div>
      <h2>{{ article }}</h2>
    </div>
  </div>
</template>

<script setup lang="ts">
const { find, baseURL } = useStrapi()
const { data: articles } = await find('procuts', {
  populate: '*',
})
</script>
<style scoped lang="scss">
.item {
  display: flex;
}
</style>