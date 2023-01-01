<template>
  <div v-if="rating >= 5" class="rating">
    {{ rating }}/5
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
  </div>
  <div v-else-if="rating >= 4" class="rating">
    {{ rating }}/5
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
  </div>
  <div v-else-if="rating >= 3" class="rating">
    {{ rating }}/5
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
  </div>
  <div v-else-if="rating >= 2" class="rating">
    {{ rating }}/5
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
  </div>
  <div v-else-if="rating >= 1" class="rating">
    {{ rating }}/5
    <div :class="{ circleWoman: woman, circleMan: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
  </div>
  <div v-else class="rating">
    {{ rating }}/5
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
    <div :class="{ circle2Woman: woman, circle2Man: man }"></div>
  </div>
</template>
<script>
export default {
  name: "RatingComponent",
  props: ["woman", "man", "rating"],
};
</script>
<style scoped>
.circleWoman {
  height: 18px;
  width: 18px;
  border: 2px solid #720060;
  background-color: #720060;
  border-radius: 50%;
  display: inline-block;
  margin-left: 5px;
}

.circle2Woman {
  height: 18px;
  width: 18px;
  border: 2px solid #720060;
  background-color: white;
  border-radius: 50%;
  display: inline-block;
  margin-left: 5px;
}

.circleMan {
  height: 18px;
  width: 18px;
  border: 2px solid #002772;
  background-color: #002772;
  border-radius: 50%;
  display: inline-block;
  margin-left: 5px;
}

.circle2Man {
  height: 18px;
  width: 18px;
  border: 2px solid #002772;
  background-color: white;
  border-radius: 50%;
  display: inline-block;
  margin-left: 5px;
}
</style>
