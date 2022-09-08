<script>
export default {
  props: ["client"],
  data: () => {
    return {
      // @todo
    };
  },
};
</script>

<template>
  <!-- About single client -->
  <div>
    <a :href="client.url"
       target="_blank">
      <img
        :src="client.img"
        :alt="client.title"
        class="
        w-64
        py-5
        px-10
        hover:bg-gray-300
        dark:hover:bg-gray-300
        border border-ternary-light
        dark:border-ternary-dark
        shadow-sm
        rounded-lg
        mb-8
        cursor-pointer
        bg-white
        dark:bg-white
      "
      />
    </a>
  </div>
</template>

<style lang="scss" scoped></style>
