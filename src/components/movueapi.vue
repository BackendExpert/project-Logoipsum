<script setup>
import { ref } from 'vue'

// ✅ Resolve local image paths properly with `new URL`
const batmanImg = new URL('../assets/Images/Batman.jpg', import.meta.url).href
const wildWestImg = new URL('../assets/Images/Wild West.jpg', import.meta.url).href
const spidermanImg = new URL('../assets/Images/Spiderman.jpg', import.meta.url).href

const searchQuery = ref('')

const movies = ref([
    {
        id: 1,
        title: 'Batman Returns',
        description:
            'Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…',
        image: batmanImg
    },
    {
        id: 2,
        title: 'Wild Wild West',
        description:
            'Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…',
        image: wildWestImg
    },
    {
        id: 3,
        title: 'The Amazing Spiderman',
        description:
            'Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…',
        image: spidermanImg
    }
])

function removeMovie(id) {
    movies.value = movies.value.filter(movie => movie.id !== id)
}

async function searchAndAdd() {
    if (!searchQuery.value.trim()) return

    const query = encodeURIComponent(searchQuery.value)
    const res = await fetch(`https://api.tvmaze.com/search/shows?q=${query}`)
    const data = await res.json()

    if (data.length > 0) {
        const show = data[0].show
        movies.value.push({
            id: Date.now(),
            title: show.name,
            description: show.summary
                ? show.summary.replace(/<[^>]+>/g, '').slice(0, 100) + '…'
                : 'No description available.',
            image: show.image?.medium || batmanImg // fallback to local if no API image
        })
        searchQuery.value = ''
    }
}
</script>

<template>
    <div class="main">
        <div class="top">
            <div class="title">
                Collect your favourites
            </div>
            <div class="search">
                <img src="../assets//Icons/Search White.svg" alt="" class="search-icon" />
                <input type="text" placeholder="Search title and add to grid" v-model="searchQuery"
                    @keyup.enter="searchAndAdd" />
            </div>
        </div>

        <hr>

        <div class="card-container">
            <div class="card" v-for="movie in movies" :key="movie.id">
                <div class="card-img-wrapper">
                    <button class="close-btn" @click="removeMovie(movie.id)"><img src="../assets/Icons/Close White.svg" alt=""></button>
                    <img :src="movie.image" alt="" class="card-img" />
                </div>
                <div class="card-content">
                    <h3>{{ movie.title }}</h3>
                    <p>{{ movie.description }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.main {
    background: #1c1c1c;
    padding: 50px 100px;
}

.top {
    display: flex;
    justify-content: space-between;
}

.top .title {
    font-size: 40px;
    color: white;
}

.search {
    display: flex;
    border: 1px solid white;
    padding: 6px 10px;
    border-radius: 6px;
}

.search-icon {
    padding: 10px;
}

.search input {
    background: transparent;
    border: none;
    width: 300px;
    height: 40px;
    padding-top: 5px;
    color: white;
}

.search input::placeholder {
    font-size: 20px;
}

hr {
    margin: 20px 0;
}

.card-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 50px;
    padding-top: 80px;
    align-items: stretch;
}

.card-container .card {
    display: flex;
    flex-direction: column;
    background: #3c3c3c;
}

.card-container .card-img-wrapper {
    flex: 1;
    display: flex;
    position: relative;
}

.card-container .card-img {
    width: 100%;
    height: auto;
    object-fit: cover;
}

.card-container .card-content {
    padding: 8px 26px;
    color: white;
}

.card-container .card-content h3 {
    font-weight: bolder;
    font-size: 22px;
}

.card-container .card-content p {
    padding-top: 10px;
    padding-bottom: 20px;
}

.close-btn {
    position: absolute;
    top: 10px;
    right: 10px;
    background: rgba(0, 0, 0, 0.6);
    color: white;
    border: none;
    font-size: 18px;
    cursor: pointer;
    padding: 4px 8px;
    border-radius: 3px;
}

@media (max-width: 1023px) {
    .card-container .card-img {
        height: 600px !important;
    }
}

@media (min-width: 768px) and (max-width: 1023px) {
    .main {
        padding: 40px 30px;
    }

    .top .title {
        font-size: 28px;
        color: white;
        padding-top: 2px;
    }

    .search-icon {
        padding: 0px;
        height: 40px;
        width: auto;
    }

    .card-container {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 767px) {
    .main {
        padding: 40px 30px;
    }

    .top {
        display: block;
    }

    .top .title {
        font-size: 20px;
        color: white;
        padding-bottom: 20px;
    }

    .search input::placeholder {
        font-size: 15px;
    }

    .card-container {
        grid-template-columns: 1fr;
    }
}
</style>
