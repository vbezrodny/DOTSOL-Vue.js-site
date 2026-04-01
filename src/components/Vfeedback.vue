<script setup>
// -1002067915593
// 7009842282:AAG1dTHw44Lx2dY9jF0gI-di7RCtdthCNZw
import {ref} from "vue";

const name = ref(""); 
const question = ref("");
const phone = ref(""); 
const email = ref("");
const success = ref(false);

async function onSubmit() {
    const botToken = "7009842282:AAG1dTHw44Lx2dY9jF0gI-di7RCtdthCNZw";
    const chatId = "-1002067915593";
    const text = `New message: %0A%0A` + 
        `Question: ${question.value} %0A` + 
        `Name: ${name.value} %0A` + 
        `Phone: ${phone.value} %0A` + 
        `Email: ${email.value} %0A`;

    //https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getMe
    await fetch(`https://api.telegram.org/bot${botToken}/sendMessage?chat_id=${chatId}&text=${text}`)
        .then((responce)=>{
            if (responce.status === 200) {
                success.value = true;
            }
        })
        .catch((error) => {
            success.value = false;
            console.log(error)
        })
        const attention = success.value ? "Sent it" : "Error! Try again.";
        alert(attention); 
        name.value = "";
        question.value = "";
        phone.value = ""; 
        email.value = "";
} 
</script>

<template>
    <section class="feedback">
            <div class="container">
                <div class="row justify-content-center">
                    <div class="col-xl-6">
                        <div class="feedback__text">
                            <h2>Остались вопросы?</h2>
                            <p>Свяжитесь с нами!</p>
                        </div>
                    </div>
                    <div class="col-lg-9 col-xl-6">
                        <form action="" class="form" method="POST" @submit.prevent="onSubmit">
                            <label class="mb-3">
                                <textarea id="textarea" placeholder="Введите ваш вопрос." title="Ваш вопрос" v-model="question" required></textarea>
                            </label>
                            <div class="form__group">
                                <label>
                                    <input placeholder="Ваше имя" type="text" title="Ваше имя" v-model="name" required>
                                </label>
                                <label>
                                    <input placeholder="+7(___)___-____" type="tel" pattern="[0-9]{11}" maxlength="11" title="Ваш телефон" v-model="phone" required>
                                </label>
                                <label>
                                    <input placeholder="Электронная почта" type="email" title="Ваша электронная почта" v-model="email" required 
                                    >
                                </label>
                            </div>
                            <button class="button-primary" type="submit">Отправить</button>
                        </form>
                    </div>
                </div>
            </div>
        </section>
</template>

<style scoped>

</style>
