<script>
import { mapState } from "vuex";
import feather from "feather-icons";

export default {
  data: () => {
    return {
      selectedSkill: "",
      searchSkill: "",
    };
  },
  computed: {
    ...mapState(["skillsHeading", "skillsDescription", "skills"]),
    filteredSkills() {
      if (this.selectedSkill) {
        return this.SkillsByCategory();
      } else if (this.searchSkill) {
        return this.SkillsBySearch();
      }
      return this.skills;
    },
  },
  methods: {
    SkillsByCategory() {
      return this.skills.filter((item) => {
        let category =
          item.category.charAt(0).toUpperCase() + item.category.slice(1);
        return category.includes(this.selectedSkill);
      });
    },
    SkillsBySearch() {
      let skill = new RegExp(this.searchSkill, "i");
      return this.skills.filter((el) => el.title.match(skill));
    },
  },
  mounted() {
    feather.replace();
  },
};
</script>

<template>
  <div class="pt-10 sm:pt-20 md:pt-24">
    <!-- Skills grid header -->
    <div class="text-center">
      <p
        class="
          font-general-semibold
          text-2xl
          sm:text-5xl
          font-semibold
          mb-2
          text-primary-dark
          dark:text-white
        "
      >
        {{ skillsHeading }}
      </p>
    </div>

    <!-- Filter and seskill -->
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
        Search skills by title or filter by category
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
        <div class="flex justify-between gap-2">
          <span
            class="
              hidden
              sm:block
              bg-primary-light
              dark:bg-primary-light
              p-2.5
              shadow-sm
              rounded-xl
              cursor-pointer
            "
          >
            <i
              data-feather="search"
              class="text-ternary-dark dark:text-ternary-light"
            ></i>
          </span>
          <input
            v-model="searchSkill"
            class="
              font-general-medium
              pl-3
              pr-1
              sm:px-4
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
            id="name"
            name="name"
            type="search"
            required=""
            placeholder="Search Skills"
            aria-label="Name"
          />
        </div>
        <SkillsFilter @change="selectedSkill = $event" />
      </div>
    </div>

    <!-- Skills grid -->
    <div class="grid grid-cols-1 sm:grid-cols-3 lg:grid-cols-5 mt-6 sm:gap-10">
      <div
        v-for="skill in filteredSkills"
        :key="skill.id"
        class="
          shadow-lg
          hover:shadow-xl
          cursor-pointer
          mb-10
          sm:mb-0
          bg-none
          dark:bg-none
        "
        aria-label="Single Skill"
      >
        <a :href="skill.url" target="_blank">
          <div>
            <img
              :src="skill.image"
              :alt="skill.title"
              height="20px"
              class="border-none"
            />
          </div>
        </a>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.skill-title{
  visibility: hidden;
}
</style>
