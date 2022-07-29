<template>
  <main>
    <section class="self-center flex flex-col flex-1 items-center justify-start">
      <img src="../assets/quirkietimes-hero.jpg" alt="" width="100%" height="100%"/>
      <h1 class="text-6xl text-center">Coming soon</h1>
    </section>
    <section class="mt-8">
      <h3 class="text-primary-600 dark:text-primary-400 max-w-5xl mx-auto">Latest issues</h3>
      <posts post-type="issue" :amount="3" />
    </section>
  </main>
</template>