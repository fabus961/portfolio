<script>
import {mapState} from "vuex";

export default {
  methods: {
    _calculateAge(dateString) {
      let birthday = +new Date(dateString);
      return ~~((Date.now() - birthday) / (31557600000));
    }
  },
  computed: {
    ...mapState(["aboutMe"]),
  },
};
</script>

<template>
  <div class="block sm:flex sm:gap-10 mt-10 sm:mt-20">
    <!-- About profile image -->
    <div class="w-full sm:w-1/4 mb-7 sm:mb-0">
      <video src="~/static/about_video.mp4" controls autoplay muted></video>
    </div>
    <!-- About details -->
    <div class="w-full sm:w-3/4 text-left">
      <h1 class="text-gray-500 dark:text-white text-4xl mb-4">Fabian Löwe</h1>
      <table class="table-fixed w-1/2 text-gray-500 dark:text-white mt-5 mb-5">
        <tbody>
        <tr>
          <td>Age</td>
          <td>{{ _calculateAge('1989-04-22') }}</td>
        </tr>
        <tr>
          <td>Languages</td>
          <td>German / English</td>
        </tr>
        <tr>
          <td>Status</td>
          <td>Open for new projects</td>
        </tr>
        </tbody>
      </table>
      <p
        v-for="bio in aboutMe"
        :key="bio.id"
        class="
          font-general-regular
          mb-4
          text-gray-500
          dark:text-white
          text-lg
        "
      >
        {{ bio.bio }}
      </p>
    </div>
  </div>
</template>
