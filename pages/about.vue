<template>
  <div>
    <AboutMe class="container mx-auto" />

    <AboutCounter />

    <AboutClients class="container mx-auto" />

    <div class="mt-5 sm:mt-14 flex justify-center">
      <a
        download=""
        href="/cv_fabian loewe.pdf"
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
        aria-label="Get my CV"
      >Get my CV
        <Button title="Get my CV"/>
      </a>
    </div>
  </div>
</template>

<style scoped></style>
