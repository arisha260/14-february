<script setup>

  import IconHeart from "@/components/icons/IconHeart.vue";
  import { ref, onMounted, computed } from "vue";

  const showText = ref(false);

  const score = ref(-1);


  const messages = [
    { text: "Привет,"},
    { text: "Привет, любимая"},
    // { text: null, image: "/img/flower.png" }, // Вместо текста появляется картинка
    { text: "Привет, любимая)"},
    { text: "Сегодня"},
    { text: "уже"},
    { text: "14"},
    { text: "февраля"},
    { text: "а"},
    { text: "это"},
    { text: "значит"},
    { text: "что"},
    { text: "сегодня"},
    { text: "праздник"},
    { text: "ЧЁЁЁЁ"},
    { text: "ЧЁЁЁЁ"},
    { text: "ЧЁЁЁЁ"},
    { text: ""},
    { text: ""},
    { text: ""},
    { text: "Я"},
    { text: "не"},
    { text: "умею"},
    { text: "красиво"},
    { text: "писать"},
    { text: "рисовать"},
    { text: "или"},
    { text: "делать"},
    { text: "что-то"},
    { text: "своими"},
    { text: "руками"},
    { text: "и"},
    { text: "в"},
    { text: "целом"},
    { text: "делать"},
    { text: "открытки"},
    { text: "но"},
    { text: "что-то"},
    { text: "сделать"},
    { text: "своими"},
    { text: "руками"},
    { text: "я"},
    { text: "всетаки"},
    { text: "хотел"},
    { text: ":)"},
    { text: ""},
    { text: "Поэтому"},
    { text: "я"},
    { text: "решил"},
    { text: "сделать"},
    { text: "для"},
    { text: "тебя"},
    { text: "такую"},
    { text: "открытку"},
    { text: "Она"},
    { text: "Она не"},
    { text: "Она не самая"},
    { text: "Она не самая оригинальная"},
    { text: "Да"},
    { text: "Да и"},
    { text: "Да и в"},
    { text: "Да и в моем"},
    { text: "представлении"},
    { text: "она"},
    { text: "все же"},
    { text: "должна"},
    { text: "должна была"},
    { text: "должна была выглядеть"},
    { text: "должна была выглядеть лучше"},
    { text: "но"},
    { text: "я"},
    { text: "честно"},
    { text: "старался"},
    { text: ":)"},
    { text: "я"},
    { text: "очень"},
    { text: "счастлив"},
    { text: "что"},
    { text: "ты"},
    { text: "у"},
    { text: "меня"},
    { text: "есть"},
    { text: ":)"},
    { text: "я"},
    { text: "тебя"},
    { text: "очень"},
    { text: "очень очень"},
    { text: "очень очень очень"},
    { text: "очень очень очень очень"},
    { text: "сильно"},
    { text: "люблю"},
    { text: "люблю!"},
    { text: "<3"},
    { text: "<3"},
    { text: "<3"},
    { text: "<3"},
    { text: "<3"},
    { text: "Спасибо"},
    { text: "Спасибо тебе"},
    { text: "Спасибо тебе за"},
    { text: "Спасибо тебе за все"},
    { text: "Спасибо тебе за все!"},
    { text: "<3"},
    { text: "Котеночек"},
    { text: "^-^"},
    { text: ""},
    { text: ""},

  ];

  // Текущий объект из массива
  const currentMessage = computed(() => messages[Math.min(score.value, messages.length - 1)]);


  onMounted(() => {
    setTimeout(() => {
      showText.value = true;
    }, 3000);
  });

</script>

<template>
  <section class="main">
    <div class="main__container container">
      <p v-if="showText && score === -1" class="main__text start-text">Кликай на сердчеко)</p>
      <p
          v-if="showText && score>=0"
          class="main__text sec-text"
          :key="score"
      >
        {{ currentMessage.text }}
      </p>
      <IconHeart class="heart" @click="score++" :class="{redHeart:score>=105}"/>

      <img v-if="score>=105" class="main__img" src="/sticker.webp" alt=")">
    </div>
  </section>
</template>

<style scoped lang="scss">

.main {
  &__container{
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    height: 100vh;
    position: relative;
  }
  &__text{
    max-width: 300px;
    margin: 0;
    color: var(--light-color);
    font-family: var(--font-family5);
    font-size: 30px;
    text-align: center;
    transition: .3s ease-in-out;
    user-select: none;
    z-index: 10;
  }
  &__span{
    display: inline-block;
  }
  &__img{
    position: absolute;
    top: 10%;
    max-width: 300px;
    animation: img 6s ease;
    user-select: none;
  }
}

.start-text{
  margin: 0;
  animation: start .5s ease;
}

.sec-text{
  animation: pulse .5s ease;
}

.heart{
  position: absolute;
  top: 55%;
  color: #FF69B4;
  animation: heartbeat 1.2s infinite ease-in-out;
  transition: .3s ease-in-out;
  z-index: 9;
}
.redHeart{
  color: #ff0000;
  animation: none;
}


@keyframes start {
  from{
    scale: 0.1;
  }
  to{
    scale: 1;
  }
}

@keyframes pulse {
  from{
    scale: 1.05;
    color: #717171;
  }
  to{
    scale: 1;
    color: #ffffff;
  }
}

@keyframes img {
  0%{
    opacity: 0;
  }
  25%{
    opacity: 0.25;
  }
  50%{
    opacity: 0.50;
  }
  75%{
    opacity: 0.75;
  }
  100%{
    opacity: 1;
  }
}

@keyframes heartbeat {
  0% {
    transform: scale(1);
  }
  30% {
    transform: scale(1.2);
  }
  50% {
    transform: scale(1);
  }
  70% {
    transform: scale(1.3);
  }
  100% {
    transform: scale(1);
  }
}

</style>