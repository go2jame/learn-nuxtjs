<template>
  <div>
    <!-- <img src="~/assets/logo.svg" /> -->
    <h1>Data fetched using asyncData</h1>
    <ul>
      <li v-for="mountain in mountains" :key="mountain.title">
        <NuxtLink
          :to="{ name: 'mountains-slug', params: { slug: mountain.slug } }"
        >
          {{ mountain.title }}
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  async asyncData() {
    const mountains = await fetch('https://api.nuxtjs.dev/mountains')
      .then((res) => res.json())
    return { mountains }
  }
}
</script>
