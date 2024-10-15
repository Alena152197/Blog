<template>
    <h1>Блог</h1>
    <main>
        <article v-for="(post, index) in posts" :key="post.id">
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
                        :to="'/category' + post.categories[0].documentId">{{ category.title }}</NuxtLink>
                </li>
            </ul>
        </article>
    </main>
</template>


<script setup>
const api = await $fetch('http://localhost:1337/api/posts?populate=*')
const posts = api.data

const base_url = "http://localhost:1337"
</script>


<style scoped>
main {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    /* grid-template-columns: repeat(auto-fit, minmax (250px, 1fr));
    grid-auto-rows: minmax(100px, auto);
    grid-template-rows: repeat(4, 1fr); */
    gap: 40px;
    padding: 40px;
}

@media screen and (max-width: 1024px) {
    .posts {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 25px;
    }
}

@media screen and (max-width: 768px) {
    .posts {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 25px;
    }
}

@media screen and (max-width: 640px) {
    .posts {
        display: grid;
        grid-template-columns: repeat(1, 1fr);
        gap: 25px;
    }
}

article {
    width: 300px;
    background-color: #f5f5f5;
    padding: 10px;

    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border: 5px solid wheat;
    border-radius: 15px;
}

article img {
    width: 100%;
    height: 150px;
    object-fit: cover;
    border-radius: 10px;
}

article p {
    height: 80px;
}

article a {
    display: block;
    text-decoration: none;
    font-weight: 500;
    border: 2px inset red;
    border-radius: 5px;
    padding: 5px;
    background-color: wheat;
    width: 100px;
    text-align: center;
}

article a:hover {
    padding: 7px;
    color: red;
}


.link {
    position: relative;
    width: 300px;
}
</style>