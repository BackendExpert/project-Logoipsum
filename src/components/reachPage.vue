<template>
    <div class="main">
        <div class="top">
            <div class="title">How to reach us</div>
            <div class="sub-title">Lorem ipsum dolor sit amet, consetetur.</div>
        </div>

        <div class="main-content">
            <div class="form">
                <form @submit.prevent="handleSubmit">
                    <div class="line1">
                        <div class="input-feild">
                            <label>First Name *</label>
                            <div>
                                <input type="text" v-model="form.firstName" :class="{ error: errors.firstName }"
                                     />
                            </div>
                            <div v-if="errors.firstName" class="error-message">
                                First name is required.
                            </div>
                        </div>

                        <div class="input-feild">
                            <label>Last Name *</label>
                            <div>
                                <input type="text" v-model="form.lastName" :class="{ error: errors.lastName }"
                                     />
                            </div>
                            <div v-if="errors.lastName" class="error-message">
                                Last name is required.
                            </div>
                        </div>
                    </div>

                    <div class="line">
                        <div class="input-feild">
                            <label>Email *</label>
                            <div>
                                <input type="email" v-model="form.email" :class="{ error: errors.email }"  />
                            </div>
                            <div v-if="errors.email" class="error-message">
                                Valid email is required.
                            </div>
                        </div>
                    </div>

                    <div class="line">
                        <div class="input-feild">
                            <label>Telephone *</label>
                            <div>
                                <input type="tel" v-model="form.telephone" />
                            </div>
                        </div>
                    </div>

                    <div class="line">
                        <div class="input-feild">
                            <label>Message *</label>
                            <div>
                                <textarea v-model="form.message" :class="{ error: errors.message }"></textarea>
                            </div>
                            <div v-if="errors.message" class="error-message">
                                Message is required.
                            </div>
                        </div>
                    </div>

                    <div class="required">* required fields</div>

                    <div class="agree-term">
                        <div>
                            <input type="checkbox" v-model="form.agree" required />
                        </div>
                        <div>
                            <p>I agree to the <a href="#">Terms & Conditions</a></p>
                        </div>
                    </div>

                    <div class="btn-container">
                        <button type="submit" class="submit-btn">SUBMIT</button>
                    </div>
                </form>
            </div>

            <div class="map">
                <iframe
                    src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d48588.133010545425!2d-3.7152472!3d40.4363503!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd422f35d4f0c269%3A0x754405946e8ca584!2sAmadeus%20IT%20Group!5e0!3m2!1sen!2slk!4v1752261080914!5m2!1sen!2slk"
                    width="100%" height="100%" style="border: 0" loading="lazy"
                    referrerpolicy="no-referrer-when-downgrade"></iframe>
            </div>
        </div>
    </div>
</template>

<script setup>
import { reactive } from "vue";

const form = reactive({
    firstName: "",
    lastName: "",
    email: "",
    telephone: "",
    message: "",
    agree: false,
});

const errors = reactive({
    firstName: false,
    lastName: false,
    email: false,
    message: false,
});

function handleSubmit() {
    errors.firstName = !form.firstName.trim();
    errors.lastName = !form.lastName.trim();
    errors.email = !form.email.trim();
    errors.message = !form.message.trim();

    if (
        !errors.firstName &&
        !errors.lastName &&
        !errors.email &&
        !errors.message
    ) {
        alert(
            `Form Submitted:\nFirst Name: ${form.firstName}\nLast Name: ${form.lastName}\nEmail: ${form.email}\nTelephone: ${form.telephone}\nMessage: ${form.message}`
        );
    }
}
</script>

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
    padding-right: 40px;
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

.map {
    padding-left: 40px;
}

@media (min-width: 768px) and (max-width: 1023px) {
    .main-content {
        display: block;
    }

    .form {
        width: 100%;
    }

    .map {
        padding-top: 40px;
        padding-left: 0;
        width: calc(100% + 200px);
        margin-left: -100px;
        position: static;
        left: auto;
        transform: none;
        height: 500px;
    }
}

@media (max-width: 767px) {
    .main {
        padding: 40px 20px;
        overflow-x: hidden;
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

    .map {
        padding-top: 40px;
        padding-left: 0;
        width: calc(100% + 200px);
        margin-left: -100px;
        position: static;
        left: auto;
        transform: none;
        height: 500px;
    }

    .line1 {
        display: block;
    }
}

.error {
    border: 2px solid red !important;
}

.error-message {
    color: red;
    font-size: 14px;
    margin-top: 4px;
}
</style>
