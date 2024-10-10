<template>
    <h1>{{ api.data.title }}</h1>

    <main>
        <div class="posts">
            <article v-for="(post, index) in posts" :key="post.id">
            <h3>{{ post.title }}</h3>
            <p>{{ post.desc }}</p>
            <NuxtLink :to="'/post/' + index">Подробнее</NuxtLink>
        </article>
        </div>
    </main>
</template>


<script setup>
const { id } = useRoute().params

const api = await $fetch('http://localhost:1337/api/categories/${id}?populate=posts.img')
// const filteredPosts = api.data.filter(post => post.id == id)
const posts = api.data.posts

const base_url = "http://localhost:1337"

const apiConfic = await $fetch(`${base_url}/api/config?populate=*`)
const config = apiConfic.data

useHead({
    title: `${api.data.title} - ${config.title}`
})



</script>