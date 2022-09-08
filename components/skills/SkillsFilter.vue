<script>
export default {
  props: {
    select: {
      type: String,
      default: "skills",
    },
    selectOptions: {
      type: Array,
      default: () => [
        "Frontend",
        "Backend",
        "Mobile",
        "Design",
        "API",
      ],
    },
  },
};
</script>

<template>
  <select
    @change="$emit('change', $event.target.value)"
    :name="select"
    :id="select"
    class="
      font-general-medium
      px-4
      py-2
      border-1 border-gray-200
      dark:border-secondary-dark
      rounded-lg
      text-sm
      sm:text-md
      bg-white
      dark:bg-white
      text-primary-dark
      dark:text-ternary-light
    "
  >
    <option value class="text-sm sm:text-md">All Skills</option>
    <option
      v-for="option in selectOptions"
      :key="option"
      :value="option"
      class="sm:text-md"
    >
      {{ option }}
    </option>
  </select>
</template>

<style lang="scss" scoped></style>
