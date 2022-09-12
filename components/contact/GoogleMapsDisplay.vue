<script>
import Button from "../reusable/Button.vue";
export default {
  components: { Button },
  data: () => {
    return {
      // @todo
    };
  },
};
</script>
<template>
  <!-- Contact form -->
  <div class="w-full md:w-1/2">
    <div
      class="
        leading-loose
        max-w-xl
        m-4
        p-7
        bg-primary-dark
        dark:bg-secondary-light
        rounded-xl
        shadow-xl
        text-left
      "
    >
      <p
        class="
          font-general-medium
          text-white
          dark:text-primary-dark
          text-2xl
          mb-8
        "
      >
        Location
      </p>
      <a href="https://goo.gl/maps/mM2YTkJ4B6yJC7ST6" target="_blank">
        <img v-if="this.$colorMode.value === 'dark'" src="/images/maps.dark.png" alt="">
        <img v-else src="/images/maps.light.png" alt="">
      </a>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
