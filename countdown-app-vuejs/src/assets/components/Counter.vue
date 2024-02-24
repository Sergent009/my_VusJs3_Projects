<template>
<div class="container" v-if="loaded">
    <div class="box">
    <section v-if="!expired">Buy Now</section>
    <section v-else>Sold Out</section>
    <div class="time">{{displayDays}} : {{displayHours}} : {{displayMinutes}} : {{displaySeconds}}</div>
    <div class="dhms"><pre>Days             Hours          Minutes         Seconds</pre></div>
</div>
</div>
</template>

<script>
export default {
    name: 'MyCounter',
    props: ['year', 'month', 'date', 'hour', 'minute', 'second', 'millisecond'],

    data(){
        return{
            displayDays: 0,
            displayHours: 0,
            displayMinutes: 0,
            displaySeconds: 0,
            loaded: false,
            expired: false
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
        },
        end(){
            return new Date(
                this.year,
                this.month,
                this.date,
                this.hour,
                this.minute,
                this.second,
                this.millisecond
            );
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
        // const endDate = new Date(2025, 1, 25, 10, 10, 10, 10)
        // the distance between start time and end time
        const distance = this.end.getTime() - newDate.getTime()

        // if the distance is less than zero. it means that the time is passed
        if(distance < 0){
            clearInterval(timer);
            this.expired = true
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
        this.loaded = true
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
    left: 430px;
}

.dhms{
    position: relative;
    top: 20px;
    left: 450px;
}

</style>