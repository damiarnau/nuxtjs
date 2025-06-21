
<template>
  <div>
    <h1 class="font-semibold text-4xl mb-8">Articles</h1>
    <ul>
    <li v-for="article in articles" :key="article.id" class="item gap-4">
      <figure>
        <VImage :image="article.thumbnail" v-if="article.thumbnail" class="img" />
      </figure>
        <div class="grid">
          <h2 class="text-2xl font-semibold">{{ article.title }}</h2>
          <div class="mt-auto font-semibold price">{{ article.price }}€</div>
        </div>
    </li>
    </ul>

  </div>
</template>

<script setup lang="ts">
const { find } = useStrapi()
const { data: articles } = await find('procuts', {
  populate: '*',
      filters: {
      active: {
        $eq: true
      }
    }
})
</script>
<style scoped lang="scss">
.item {
  position: relative;
  // display: flex;
}
.price {
  color: #c75f15; 
  position: absolute;
  z-index: 1;
  bottom: 2rem;
  right: 0;
  width: 2rem;
  text-align: center;
  &:before{
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    width: 3rem;
    height: 3rem;
    border-radius: 3rem;
    transform: translate(-50%, -50%);
    background-color: #dbdbdb;
    z-index: -1;
  }
}
figure {
  background-color: #be682a;
  border-radius: 10px;
  overflow: hidden;
}
.img {
  width: 200px;
  height: 200px;
  object-fit: cover;
  
  
      filter: drop-shadow(4px 2px 3px #502b04);
}
ul {
      display: flex;
      flex-wrap: wrap;
    gap: 32px;
}
</style>