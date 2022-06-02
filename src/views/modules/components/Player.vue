<template>
    <div class="training">
        <div class="card bg-laravel">
            <span class="icon">
                <img src="images/icons/laravel.svg" alt="">
            </span>
            <span class="title">Aula 01 - Leonardo</span>
            <router-link :to="{ name: 'campus.home' }" :class="['btn', 'laravel', 'fas', 'fa-chevron-left']">
                Voltar
            </router-link>
        </div>

        <iframe width="100%" height="auto" src="https://www.youtube.com/embed/tC7_0X6oS-Q" title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen>
        </iframe>

    </div>
</template>

<script>
export default {
    name: "Player"
}
</script>