<template>
    <nav>
        <ul>
            <li>
                <NuxtLink to="/">Главная</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/blog">Блог</NuxtLink>
            </li>
            <li>
                <NuxtLink to="/contact">Контакты</NuxtLink>
            </li>
        </ul>
    </nav>
</template>

<style scoped>

nav {
    background-color: rgb(247, 175, 92);
    padding: 5px;
    border-radius: 10px;
    
}

ul {
    list-style: none;
    display: flex;
    gap: 20px;
    padding: 0;
}

li a {
    color: black;
    text-decoration: none;
    font-weight: 700;
}

li a:hover {
    border: 3px inset red;
    border-radius: 5px;
    padding: 5px;
    background-color: wheat;
    
} 


</style>