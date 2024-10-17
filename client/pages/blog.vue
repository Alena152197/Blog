<template>
    <h1>Блог</h1>
    <main>
        <div class="articles">
            <article v-for="(post, index) in posts" :key="post.id"
                class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
                <a href="#">
                    <img class="rounded-t-lg" :src="base_url + post.img[0].url" :alt="post.img[0].alternativeText" />
                </a>
                <div class="p-5">
                    <NuxtLink :to="'/post/' + post.documentId">
                        <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ post.title }}</h5>
                    </NuxtLink>
                    <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">{{ post.desc }}</p>
                    <NuxtLink :to="'/post/' + post.documentId">
                        <p class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                        Подробнее
                        <svg class="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true"
                            xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M1 5h12m0 0L9 1m4 4L9 9" />
                        </svg>
                    </NuxtLink>
                </div>
            </article>
        </div>


        <!-- <article v-for="(post, index) in posts" :key="post.id">
            <h3>{{ post.title }}</h3>
            <div class="link">
                <img :src="base_url + post.img[0].url" :alt=post.img[0].alternativeText>
                <NuxtLink :style="'background:' + post.categories[0].url" :to="'/post/' + post.documentId">Подробнее
                </NuxtLink>
            </div>
            <p>{{ post.desc }}</p>
            <ul class="tag">
                <li v-for="(category, index) in post.categories" :key="category.id">
                    <NuxtLink :style="'background:' + post.categories[index].bg"
                        :to="'/category/' + post.categories[0].documentId">{{ category.title }}</NuxtLink>
                </li>
            </ul>
        </article> -->
    </main>
</template>


<script setup>
const api = await $fetch('http://localhost:1337/api/posts?populate=*')
const posts = api.data

const base_url = "http://localhost:1337"
</script>
