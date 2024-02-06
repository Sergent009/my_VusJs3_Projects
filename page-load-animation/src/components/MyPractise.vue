<template>
    <div class="box"></div>
    <div class="box2"></div>
    <div class="box3"></div>
</template>

<script>
export default {
    name: 'MyPractise'
}
</script>

<style>
.box{
    width: 60px;
    height: 60px;
    background: skyblue;
    position: absolute;
    top: 0;
    left: 0;
    
    animation: right linear 3s 1;
}
@keyframes right {
    100% {transform: translateX(1240px);}
}

.box2{
    width: 60px;
    height: 60px;
    background: blue;
    position: absolute;
    top: 0;
    left: 0;

    animation: down linear 3s 1;
}
@keyframes down {
    100% {transform: translateY(610px);}
}

.box3{
    width: 60px;
    height: 60px;
    background: purple;
    position: absolute;
    top: 0;
    left: 0;

    animation: another linear 3s 1;
}
@keyframes another {
    100% {transform: translate3d(300deg)}
}
</style>