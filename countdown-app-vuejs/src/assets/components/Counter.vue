<template>
<div class="container">
    <div class="box">
        <section>Buy Now</section>
    <div class="time">{{displayDays}} : {{displayHours}} : {{displayMinutes}} : {{displaySeconds}}</div>
    <div class="dhms"><pre> Days      Hours      Minutes     Seconds</pre></div>
</div>
</div>
</template>

<script>
export default {
    name: 'MyCounter',

    data(){
        return{
            displayDays: 0,
            displayHours: 0,
            displayMinutes: 0,
            displaySeconds: 0
        }
    },

    computed: {
        seconds: () => 1000,
        minutes(){
            return this.seconds * 60
        },
        hours(){
            return this.minutes * 60
        },
        days(){
            return this.hours * 24
        }
    },

    methods: {
    formatNumber(num) {
        return num < 10 ? '0' + num : num
    },
    showRemaining(){
        const timer = setInterval(() => {
        // current data
        const newDate = new Date()
        // when the timer will end
        const endDate = new Date(2025, 1, 25, 10, 10, 10, 10)
        // the distance between start time and end time
        const distance = endDate.getTime() - newDate.getTime()

        // if the distance is less than zero. it means that the time is passed
        if(distance < 0){
            clearInterval(timer);
             return
        }

        const days = Math.floor(distance / this.days)
        const hours = (Math.floor(distance % this.days) / this.hours).toFixed(0)
        const minutes = (Math.floor(distance % this.hours) / this.minutes).toFixed(0)
        const seconds = (Math.floor(distance % this.minutes) / this.seconds).toFixed(0)

        this.displayMinutes = this.formatNumber(minutes)
        this.displaySeconds = this.formatNumber(seconds)
        this.displayHours = this.formatNumber(hours)
        this.displayDays = this.formatNumber(days)
    }, 1000)
    }
    },

    mounted(){
        this.showRemaining()
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Anta&display=swap');

.container{
    position: absolute;
    top: 0;
    left: 0;
    font-family: "Anta", sans-serif;
}


.time{
    font-size: 60px;
    position: relative;
    top: 40px;
    left: 500px;
}

.dhms{
    position: relative;
    top: 40px;
    left: 500px;
}

</style>