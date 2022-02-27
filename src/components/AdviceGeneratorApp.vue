<template>
  <div class="layout">
    <main v-if="!loading && advice" class="advice-card">
      <h1 class="advice-card__heading">ADVICE #{{ advice.slip.id }}</h1>
      <p class="advice-card__body">"{{ advice.slip.advice }}"</p>
      <figure class="advice-card__divider">
        <img
          v-if="isMobile"
          class="advice-card__divider-img"
          src="@/assets/pattern-divider-mobile.svg"
          alt="Divider of card"
          height="16"
          width="295"
        />
        <img
          v-else
          class="advice-card__divider-img"
          src="@/assets/pattern-divider-desktop.svg"
          alt="Divider of card"
          height="16"
          width="444"
        />
      </figure>
      <figure class="advice-card__dice">
        <img
          class="advice-card__dice-img"
          src="../assets/icon-dice.svg"
          alt="Die with five dots"
          height="24"
          width="24"
        />
      </figure>
    </main>
  </div>
</template>

<script setup>
import { computed } from "vue";
import { useFetch, useMediaQuery } from "@vueuse/core";

const { isFetching, data } = useFetch("https://api.adviceslip.com/advice");

const isMobile = useMediaQuery("(max-width: 600px)");

const advice = computed(() =>
  data.value ? JSON.parse(data.value) : undefined
);

const loading = computed(() => isFetching.value);
</script>

<style scoped lang="scss">
.layout {
  background-color: var(--dark-blue);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vw;
  padding: 0 1rem;
}
.advice-card {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: var(--dark-grayish-blue);
  max-width: 33.75rem;
  border-radius: 0.9375rem;
  padding: 1.5rem;
  @media only screen and (min-width: 600px) {
    padding: 3rem;
  }
  &__heading {
    color: var(--neon-green);
    font-size: 0.8125rem;
    letter-spacing: 4.09px;
    word-spacing: 1;
  }
  &__body {
    color: var(--light-cyan);
    font-size: 1.75rem;
    line-height: 1.3;
    margin-top: 1.5rem;
    margin-bottom: 1.5rem;
    letter-spacing: -0.5px;
    @media only screen and (min-width: 600px) {
      margin-bottom: 2.5rem;
      letter-spacing: -0.3px;
    }
  }
  &__divider {
    margin: 0 0 1.5rem;
  }
  &__dice {
    position: absolute;
    bottom: -2rem;
    margin: 0;
    border-radius: 50%;
    background: var(--neon-green);
    width: 4rem;
    height: 4rem;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
