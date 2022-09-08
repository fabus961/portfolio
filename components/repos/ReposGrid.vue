<script>
export default {
  data: () => {
    let repos = [];

    return {
      repos,
    };
  },

  computed: {
    filteredRepos() {
      return this.repos;
    },
  },
  created() {
    fetch("https://api.github.com/users/fabus961/repos")
      .then(response => response.json())
      .then(data => (this.repos = data));
  }
}
</script>

<template>
  <div class="container grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-2 mt-6 sm:gap-10">
    <div
      v-for="repo in filteredRepos"
      :key="repo.id"
      class="
          rounded-xl
          shadow-lg
          hover:shadow-xl
          cursor-pointer
          mb-10
          sm:mb-0
          bg-primary-dark
          dark:bg-secondary-light
        "
      aria-label="Single Repo"
    >
      <div class="p-4">
        <!--Card 1-->
        <div class="w-full lg:max-w-full lg:flex">
          <div
            class="h-48 lg:h-auto lg:w-48 flex-none bg-cover rounded-t lg:rounded-t-none lg:rounded-l text-center overflow-hidden"
            title="GitHub Logo">
            <img
              v-if="$colorMode.value === 'dark'"
              src="/images/github_purple.png" alt="">
            <img
              v-else
              src="/images/github_white.png" alt="">
          </div>
          <div
            class="bg-primary-dark dark:bg-secondary-light rounded-b lg:rounded-b-none lg:rounded-r p-4 flex flex-col justify-between leading-normal">
            <div class="mb-8">
              <p class="text-sm text-white dark:text-primary-dark flex items-center">
                <svg class="fill-current text-white dark:text-primary-dark w-3 h-3 mr-2"
                     xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                  <path
                    d="M4 8V6a6 6 0 1 1 12 0v2h1a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2v-8c0-1.1.9-2 2-2h1zm5 6.73V17h2v-2.27a2 2 0 1 0-2 0zM7 6v2h6V6a3 3 0 0 0-6 0z"/>
                </svg>
                {{ repo.updated_at }}
              </p>
              <div class="text-white font-bold text-xl dark:text-primary-dark mb-2">{{ repo.name }}</div>
              <p class="text-white text-base dark:text-primary-dark">
                <a :href="repo.html_url"
                   target="_blank"
                >{{ repo.html_url }}</a>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>
