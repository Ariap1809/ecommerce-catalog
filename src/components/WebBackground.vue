<template>
    <div :class="{ BackgroundWoman: data.woman, BackgroundMan: data.man, Background: data.unavaliable }"></div>

</template>
<script>
export default {
    name: "WebBackgorund",
    props: ["dataComponent"],
    data() {
        return {
            title: "data",
            data: this.dataComponent,
        };
    },
};
</script>
<style scoped>
.BackgroundWoman {
    position: fixed;
    top: 0px;
    z-index: -1;
    width: 100vw;
    height: 66vh;
    background-color: #fde2ff;
    background-image: url("../assets/bg-pattern.svg");
}

.BackgroundMan {
    position: fixed;
    top: 0px;
    z-index: -1;
    width: 100vw;
    height: 66vh;
    background-color: #d6e6ff;
    background-image: url("../assets/bg-pattern.svg");
}

.Background {
    position: fixed;
    top: 0px;
    z-index: -1;
    width: 100vw;
    height: 66vh;
    background-color: #DCDCDC;
}
</style>
