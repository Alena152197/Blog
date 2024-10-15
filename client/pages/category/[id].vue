<template>
    <h1>{{ api.data.title }}</h1>

    <main>
        <article v-for="(post, index) in posts" :key="post.id">
            <h3>{{ post.title }}</h3>
            <div class="link">
                <img :src="base_url + post.img[0].url" :alt=post.img[0].alternativeText>
                <NuxtLink :style="'background:' + api.data.bg" :to="'/post/' + post.documentId">Подробнее</NuxtLink>
            </div>
            <p>{{ post.desc }}</p>
            <ul class="tag">
                <li v-for="(category, index) in post.categories" :key="category.id">
                    <NuxtLink :style="'background:' + post.categories[index].bg"
                        :to="'/category' + post.categories[0].documentId">{{ category.title }}</NuxtLink>
                </li>
            </ul>
        </article>
    </main>
</template>


<script setup>
const { id } = useRoute().params

const api = await $fetch(`http://localhost:1337/api/categories/${id}?populate=posts.img&populate=posts.categories`)
// const filteredPosts = api.data.filter(post => post.id == id)
const posts = api.data.posts

const base_url = 'http://localhost:1337'

const apiConfic = await $fetch(`${base_url}/api/config?populate=*`)
const config = apiConfic.data

useHead({
    title: `${api.data.title} - ${config.title}`
})



</script>