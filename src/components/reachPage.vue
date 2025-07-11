<template>
    <div class="main">
        <div class="top">
            <div class="title">
                How to reach us
            </div>
            <div class="sub-title">
                Lorem ipsum dolor sit amet, consetetur.
            </div>
        </div>

        <div class="main-content">
            <div class="form">
                <form action="" method="post">
                    <div class="line1">
                        <div class="input-feild">
                            <label for="First Name ">First Name *</label>
                            <div class="">
                                <input type="text" required>
                            </div>
                        </div>
                        <div class="input-feild">
                            <label for="Last Name ">Last Name *</label>
                            <div class="">
                                <input type="text" required>
                            </div>
                        </div>
                    </div>

                    <div class="line">
                        <div class="input-feild">
                            <label for="Email ">Email *</label>
                            <div class="">
                                <input type="email" required>
                            </div>
                        </div>
                    </div>

                    <div class="line">
                        <div class="input-feild">
                            <label for="Telephone ">Telephone *</label>
                            <div class="">
                                <input type="email" required>
                            </div>
                        </div>
                    </div>

                    <div class="line">
                        <div class="input-feild">
                            <label for="Message ">Message *</label>
                            <div class="">
                                <textarea name="" id=""></textarea>
                            </div>
                        </div>
                    </div>

                    <div class="required">
                        * required fields
                    </div>

                    <div class="agree-term">
                        <div class="">
                            <input type="checkbox" name="" id="">
                        </div>
                        <div class="">
                            <p class="">I agree to the <a href="#">Terms & Conditions</a></p>
                        </div>
                    </div>

                    <div class="btn-container">
                        <button type="submit" class="submit-btn">
                            SUBMIT
                        </button>
                    </div>
                </form>
            </div>
            <div class="map">

            </div>
        </div>
    </div>
</template>

<style scoped>
.main {
    padding: 50px 100px;
    background: #000;
    color: white;
}

.top .title {
    font-size: 30px;
    padding-bottom: 15px;
    letter-spacing: 2px;
}

.top .sub-title {
    font-size: 15px;
    padding-bottom: 15px;
    letter-spacing: 4px;
    color: gray;
}

.main-content {
    display: flex;
    justify-content: space-between;
}

.form {
    width: 70%;
}

.map {
    width: 100%;
}

.line {
    width: 100%;
    margin: 20px 0;
}

.line1 {
    width: 100%;
    margin: 20px 0;
    display: flex;
    gap: 50px;
}

.input-feild {
    width: 100%;
}

.input-feild label {
    color: gray;
}

.input-feild input {
    width: 100%;
    height: 50px;
    margin-top: 4px;
    border-radius: 5px;
    border: none;
    background-color: #3c3c3c;
    font-size: 20px;
    color: white;
    padding-left: 10px;
}

.input-feild textarea {
    width: 100%;
    height: 100px;
    margin-top: 4px;
    border-radius: 5px;
    border: none;
    background-color: #3c3c3c;
    font-size: 20px;
    color: white;
    padding-left: 10px;
}

.required {
    color: gray;
}

.agree-term {
    display: flex;
    margin-top: 20px;
}

.agree-term a {
    color: white;
}

input[type="checkbox"] {
    width: 20px;
    height: 20px;
    margin-right: 8px;
    accent-color: #cc9500;
    cursor: pointer;
    background-color: transparent;
    border: 1px solid white;
    border-radius: 4px;
    appearance: none;
    -webkit-appearance: none;
    outline: none;
    transition: all 0.2s ease;
}



input[type="checkbox"]:checked {
    background-color: #cc9500;
    border-color: #cc9500;
}


input[type="checkbox"]:checked::after {
    content: "✔";
    color: white;
    font-size: 14px;
    display: block;
    text-align: center;
    line-height: 20px;
}

.btn-container {
    display: flex;
    justify-content: flex-end;
    margin-top: 40px;
}

.submit-btn {
    background-color: #cc9500;
    color: white;
    padding: 10px 50px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

@media (min-width: 768px) and (max-width: 1023px) {
    .main-content {
        display: block;
    }

    .form {
        width: 100%;
    }
}


@media (max-width: 767px) {
    .main {
        padding: 40px 30px;
    }

    .main-content {
        display: block;
    }

    .form {
        width: 100%;
    }

    .line1 {
        display: block;
    }

    .input-feild {
        margin-top: 8px;
    }

    .btn-container {
        justify-content: center;
    }
}
</style>