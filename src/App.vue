<script setup>
import '@/assets/css/style.css'
</script>

<template>
    <div class="wrapper">
        <div class="rating" v-show="state == 'rating'">
            <img src="@/assets/img/icon-star.svg" alt="star">
            <h1>How did we do?</h1>
            <p>Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!</p>
            <div class="rating__scale">
                <button @click="rating = 1" :class="{ 'active': rating == 1 }">1</button>
                <button @click="rating = 2" :class="{ 'active': rating == 2 }">2</button>
                <button @click="rating = 3" :class="{ 'active': rating == 3 }">3</button>
                <button @click="rating = 4" :class="{ 'active': rating == 4 }">4</button>
                <button @click="rating = 5" :class="{ 'active': rating == 5 }">5</button>
            </div>
            <button class="rating__submit" @click="ratingSubmit()">Submit</button>
        </div>
        <Transition>
            <div class="thank-you" v-show="state == 'thank you'">
                <img src="@/assets/img/illustration-thank-you.svg" alt="phone">
                <span>You selected {{ rating }} out of 5</span>
                <h1>Thank you!</h1>
                <p>We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in touch!</p>
            </div>
        </Transition>
        <div class="attribution">
            Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
            Coded by <a href="https://momboteq.github.io">MomboteQ</a>.
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            state: 'rating',
            rating: 0
        }
    },
    methods: {
        ratingSubmit() {
            if (this.rating > 0) {
                this.state = 'thank you'
            }
        }
    }
}
</script>