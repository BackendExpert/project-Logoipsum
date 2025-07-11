<template>
    <footer>
        <div class="top-content">
            <div class="left">
                <h3 class="">Amadeus IT Group</h3>
                <div class="">
                    <p class="">
                        C. Salvador de Madariaga, 1 <br>
                        28027 Madrid <br>
                        Spain <br>
                    </p>
                </div>
            </div>


            <div class="right">
                <div class="social">
                    <h3 class=""> Follow us on</h3>
                    <img src="../assets/Icons/Twitter White.svg" alt="">
                    <img src="../assets/Icons/Youtube White.svg" alt="">
                </div>
            </div>
        </div>

        <hr>

        <div class="lower-content">
            <div class="">
                Copyright &copy; {{ currentYear }} Amadeus Hotels. All rights reserved.
            </div>
            <div class="photo-by">
                Photos by <a href="#">Felix Mooneeram</a> & <a href="#">Serge Kutuzov</a> on <a href="#">Unsplash</a>
            </div>
        </div>
    </footer>
</template>


<style scoped>
footer {
    background: #1c1c1c;
    color: white;

}

.top-content {
    display: flex;
    justify-content: space-between;
    padding: 50px 100px;
}

.top-content .left h3 {
    padding-bottom: 10px;
    font-size: 25px;
}

.top-content .left p {
    color: gray;
}

.top-content .right .social {
    display: flex;
    gap: 20px;
}

.top-content .right h3 {
    padding-bottom: 10px;
    font-size: 25px;
    padding-top: 4px;
}

hr {
    border: 1px solid rgb(77, 77, 77);
}

.lower-content {
    padding: 20px 100px;
    display: flex;
    justify-content: space-between;
    color: gray;
}

.lower-content a {
    color: white;
}



@media (min-width: 768px) and (max-width: 1023px) {
    .top-content {
        padding: 40px 100px;
    }

    .lower-content {
        display: block;
        justify-content: center;
        text-align: center;
    }

    .lower-content .photo-by {
        padding-top: 10px;
    }
}

@media (max-width: 767px) {
    .top-content {
        display: block;
        padding: 40px 30px;
    }

    .top-content .left h3,
    p {
        text-align: center;
    }

    .top-content .right .social {
        padding-top: 20px;
        justify-content: center;
    }

    .lower-content {
        padding: 40px 30px;
        display: block;
        justify-content: center;
        text-align: center;
    }

    .lower-content .photo-by {
        padding-top: 10px;
    }
}
</style>


<script>
export default {
    data() {
        return {
            currentYear: new Date().getFullYear()
        };
    }
};
</script>
