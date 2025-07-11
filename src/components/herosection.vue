<template>
    <div class="main-content">
        <video src="../assets/Videos/Header Video.mp4" autoplay muted loop playsinline class="header-video"></video>

        <div class="text-content">
            <h1 class=""> MOVIE LIBRARY</h1>
            <p class="">
                Lorem ipsum dolor sit amet, consetetur sadipscing elitr, <br>
                sed diam nonumy eirmod tempor invidunt ut labore et <br>
                dolore magna aliquyam erat, sed diam voluptua. <br>
            </p>
        </div>
    </div>
</template>

<style scoped>
.main-content {
    background: #000;
    color: white;
}

.header-video {
    width: 100%;
    height: 70vh;
    display: block;
    object-fit: cover;
    border-bottom: 1px solid rgb(37, 37, 37);
}

.text-content {
    padding: 70px 100px;
}

.text-content h1 {
    font-size: 50px;
}

.text-content p {
    padding-top: 15px;
    font-size: 20px;
    word-spacing: 2px;
    letter-spacing: 4px;
    color: gray;
}

@media (min-width: 768px) and (max-width: 1023px) {
    .text-content {
        padding: 40px 30px;
    }

    .text-content p {
        font-size: 16px;
    }

}


@media (max-width: 767px) {
    .text-content {
        padding: 40px 30px;
    }

    .text-content h1 {
        font-size: 30px;
    }

    .text-content p {
        font-size: 16px;
    }
}
</style>
