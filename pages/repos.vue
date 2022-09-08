<script>
import ReposGrid from "~/components/repos/ReposGrid";

export default {
  components: {
    ReposGrid
  },
};
</script>

<template>
  <div class="pt-10 sm:pt-20 md:pt-24">
    <!-- Repos grid header -->
    <div class="text-center">
      <p
        class="
          font-general-semibold
          text-2xl
          sm:text-5xl
          font-semibold
          mb-5
          text-primary-dark
          dark:text-white
        "
      >
        REPOS
      </p>
    </div>
    <div class="mt-8 sm:mt-10">
      <h3
        class="
          font-general-regular
          text-center text-primary-dark
          dark:text-white
          text-md
          sm:text-xl
          font-normal
          mb-4
        "
      >
        An overview of my personal repositories
      </h3>
      <div
        class="
          flex
          justify-between
          border-b border-primary-light
          dark:border-secondary-dark
          pb-3
          gap-2
        "
      >
      </div>
    </div>

    <!-- Repos grid -->
    <ReposGrid />

    <div class="mt-5 sm:mt-14 flex justify-center">
      <NuxtLink
        to="/about"
        class="
          font-general-medium
          flex
          items-center
          px-6
          py-3
          rounded-lg
          shadow-lg
          hover:shadow-xl
          bg-indigo-500
          hover:bg-indigo-600
          focus:ring-1 focus:ring-indigo-900
          text-white text-lg
          sm:text-xl
          duration-300
        "
        aria-label="About Me"
      >About Me
        <Button title="About Me"/>
      </NuxtLink>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
