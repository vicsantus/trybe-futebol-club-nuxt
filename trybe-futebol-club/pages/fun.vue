<template>
  <div>
    <NuxtLink to="/">Home</NuxtLink>
    <p v-if="$fetchState.pending">Fetching mountains...</p>
    <p v-else-if="$fetchState.error">An error occurred :(</p>
    <div v-else>
      <h1>Nuxt Mountains</h1>
      <ul>
        <li v-for="mountain of mountains" :key="mountain.id">
          {{ mountain.title }}
          <img :src="mountain.image" class="mountain-img" :alt="mountain.title" />
        </li>
      </ul>
      <button @click="$fetch">Refresh</button>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        mountains: []
      }
    },
    async fetch() {
      this.mountains = await fetch(
        'https://api.nuxtjs.dev/posts'
      ).then(res => res.json())
    }
  }
</script>

<style>
.mountain-img {
  max-height: 450px;
}
</style>
