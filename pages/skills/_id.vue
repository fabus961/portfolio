<script>
import feather from "feather-icons";
export default {
  scrollToTop: true,
  data: () => {
    return {
      // @todo
    };
  },
  computed: {
    skill() {
      return this.$store.getters.getSkillById(this.$route.params.id);
    },
  },
  mounted() {
    feather.replace();
  },
  updated() {
    feather.replace();
  },
};
</script>

<template>
  <div class="container mx-auto">
    <!-- Check if there are skills and then load -->
    <div v-if="skill">
      <!-- Skill heading and meta info -->
      <div>
        <p
          class="
            font-general-medium
            text-left text-3xl
            sm:text-4xl
            font-bold
            text-primary-dark
            dark:text-white
            mt-14
            sm:mt-20
            mb-7
          "
        >
          {{ skill.title }}
        </p>
        <div class="flex">
          <div class="flex items-center mr-10">
            <i
              data-feather="clock"
              class="w-4 h-4 text-gray-500 dark:text-white"
            ></i>
            <span
              class="
                font-general-medium
                ml-2
                leading-none
                text-primary-dark
                dark:text-white
              "
            >{{ skill.publishDate }}</span
            >
          </div>
          <div class="flex items-center">
            <i
              data-feather="tag"
              class="w-4 h-4 text-gray-500 dark:text-white"
            ></i>
            <span
              class="
                font-general-medium
                ml-2
                leading-none
                text-primary-dark
                dark:text-white
              "
            >{{ skill.tag }}</span
            >
          </div>
        </div>
      </div>

      <!-- Skill gallery -->
      <div class="grid grid-cols-1 sm:grid-cols-3 sm:gap-10 mt-12">
        <div
          class="mb-10 sm:mb-0"
          v-for="skillImage in skill.skillImages"
          :key="skillImage.id"
        >
          <img
            :src="skillImage.img"
            class="rounded-xl cursor-pointer shadow-lg sm:shadow-none"
          />
        </div>
      </div>

      <!-- Skill info -->
      <div class="block sm:flex gap-0 sm:gap-10 mt-14">
        <!-- Single skill left section details -->
        <div class="w-full sm:w-1/3 text-left">
          <!-- Single skill client details -->
          <div class="mb-7">
            <p
              class="
                font-general-medium
                text-2xl text-gray-500
                dark:text-white
                mb-2
              "
            >
              {{ skill.clientTitle }}
            </p>
            <ul class="leading-loose">
              <li
                v-for="info in skill.companyInfos"
                :key="info.id"
                class="
                  font-general-regular
                  text-gray-500
                  dark:text-white
                "
              >
                <span>{{ info.title }}: </span>
                <a
                  href="#"
                  :class="
                    info.title == 'Website' || info.title == 'Phone'
                      ? 'hover:underline cursor-pointer'
                      : ''
                  "
                  aria-label="Skill website and phone"
                >{{ info.details }}</a
                >
              </li>
            </ul>
          </div>

          <!-- Single skill objectives -->
          <div class="mb-7">
            <p
              class="
                font-general-medium
                text-2xl text-gray-500
                dark:text-white
                mb-2
              "
            >
              {{ skill.objectivesTitle }}
            </p>
            <p
              class="
                font-general-regular
                text-primary-dark
                dark:text-white
              "
            >
              {{ skill.objectivesDetails }}
            </p>
          </div>

          <!-- Single skill technologies -->
          <div class="mb-7">
            <p
              class="
                font-general-medium
                text-2xl text-gray-500
                dark:text-white
                mb-2
              "
            >
              {{ skill.techTitle }}
            </p>
            <p
              class="
                font-general-regular
                text-primary-dark
                dark:text-white
              "
            >
              {{ skill.technologies.join(", ") }}
            </p>
          </div>

          <!-- Single skill social sharing -->
          <div>
            <p
              class="
                font-general-medium
                text-2xl text-gray-500
                dark:text-white
                mb-2
              "
            >
              {{ skill.socialTitle }}
            </p>
            <div class="flex items-center gap-3 mt-5">
              <a
                v-for="social in skill.socialSharings"
                :key="social.id"
                :href="social.url"
                target="__blank"
                aria-label="Share Skill"
                class="
                  bg-primary-light
                  dark:bg-secondary-light
                  dark:text-primary-dark
                  text-secondary-light
                  hover:text-primary-light
                  dark:hover:text-primary-light
                  p-2
                  rounded-lg
                  shadow-sm
                  duration-500
                "
              ><i
                :data-feather="social.icon"
                class="w-4 lg:w-5 h-4 lg:h-5"
              ></i
              ></a>
            </div>
          </div>
        </div>

        <!-- Single skill right section details -->
        <div class="w-full sm:w-2/3 text-left mt-10 sm:mt-0">
          <p
            class="
              font-general-medium
              text-gray-500
              dark:text-white
              text-2xl
              font-bold
              mb-7
            "
          >
            {{ skill.detailsTitle }}
          </p>
          <p
            v-for="skillDetail in skill.skillDetails"
            :key="skillDetail.id"
            class="
              font-general-regular
              mb-5
              text-lg text-gray-500
              dark:text-white
            "
          >
            {{ skillDetail.details }}
          </p>
        </div>
      </div>

    </div>

    <!-- Load not found components if no skill found -->
    <div v-else class="font-general-medium container mx-auto text-center">
      <h1>No skills yet</h1>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
