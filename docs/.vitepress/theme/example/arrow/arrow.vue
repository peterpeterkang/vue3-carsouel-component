<template>
  <base-usage
    :code="usageCode"
    :config-list="configList"
    :panel-list="panelList"
    @panel-change="onPanelChange"
  >
    <template #swiper="{ configProps }">
      <div :style="{ width: '800' }">
        <carousel
          ref="carousel"
          class="carousel"
          transitionStyle="all 300ms linear"
          :direction="configProps.direction"
          :effect="configProps.effect"
          :showDots="configProps.showDots"
          :showArrow="configProps.showArrow"
          :dotPlacement="configProps.dotPlacement"
          :arrowPlacement="configProps.arrowPlacement"
          :turnDirection="configProps.turnDirection"
          :autoplay="false"
          :delay="0"
          :loop="true"
          :defaultIndex="0"
          :trigger="'hover'"
        >
          <img src="https://jiazhiheng.github.io/vue3-carsouel-component/images/1.webp" />
          <img src="https://jiazhiheng.github.io/vue3-carsouel-component/images/2.webp" />
          <img src="https://jiazhiheng.github.io/vue3-carsouel-component/images/3.webp" />
          <img src="https://jiazhiheng.github.io/vue3-carsouel-component/images/4.webp" />
          <img src="https://jiazhiheng.github.io/vue3-carsouel-component/images/5.webp" />
          <img src="https://jiazhiheng.github.io/vue3-carsouel-component/images/6.webp" />
          <img src="https://jiazhiheng.github.io/vue3-carsouel-component/images/7.webp" />
          <img src="https://jiazhiheng.github.io/vue3-carsouel-component/images/8.webp" />
        </carousel>
      </div>
    </template>
  </base-usage>
</template>

<script setup lang="jsx">
/* eslint-disable */
import { ref, onMounted } from 'vue';
import configJson from './props.json';
import { cardListConfig } from './card.js';

const cardList = ref(cardListConfig);
const configList = ref(configJson);
const panelList = [{ label: 'swiper', value: 'swiper' }];

const usageCodeMap = {
  swiper: `<carousel
          ref="carousel"
          class="carousel"
          transitionStyle="all 300ms linear"
          :showDots="configProps.showDots"
          :showArrow="configProps.showArrow"
          :effect="'slide'"
          :delay="4000"
          :loop="true"
          @change="pageChange($event)"
        ><div v-for="item in cardList" :style="item.style"></div>
        </carousel>`
};

const usageCode = ref(`<template>${usageCodeMap[panelList[0].value].trim()}</template>`);

function onPanelChange(panel) {
  usageCode.value = `<template>${usageCodeMap[panel].trim()}</template>`;
}
</script>

<style scoped>
.carousel {
  width: 480px;
  height: 270px;
  overflow: hidden;
}

img {
  width: 480px;
  height: 270px;
  object-fit: cover;
  display: block;
}
</style>
