<template>
<section class="mx-auto w-full">
  <div class="mx-auto w-full">
    <img src="../../assets/quirkietimes-pagetop.jpeg" alt="" width="100%" height="100%"/>
  </div>
  <nav class="pt-6 mt-9 px-6 max-w-7xl mx-auto" aria-label="Main Menu">
    <div class="main-heading flex justify-center items-center pt-6">
       <h1 class="text-3xl md:text-5xl lg:text-7xl">THE QUIRKIE TIMES</h1>
    </div>
    <div class="flex justify-start items-end">
       <p class="text-base capitalize">Since 2022</p>
    </div>
    <div class="navlist flex justify-center items-center">
      <ul class="flex flex-wrap justify-center ">
        <li class="list_inline flex justify-center items-center">
          <h4 class="font-bold">Quirkies</h4>
        </li>
        <li class="list_inline flex justify-center items-center">
          <h4 class="font-bold">Quirklings</h4>
        </li>
        <li class="list_inline flex justify-center items-center">
          <h4 class="font-bold">NFTs</h4>
        </li>
        <li class="list_inline flex justify-center items-center">
          <h4 class="font-bold">Web3</h4>
        </li>
        <li class="list_inline flex justify-center items-center">
          <h4 class="font-bold">Puzzles</h4>
        </li>
        <li class="list_inline flex justify-center items-center">
          <h4 class="font-bold">ETH</h4>
        </li>
        <li class="list_inline flex justify-center items-center">
          <h4 class="font-bold">Web3 Safety</h4>
        </li>
      </ul>
    </div>
  </nav>
</section>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="postcss" scoped>
.main-heading {
  h1 {
    letter-spacing: 3px;
  }
}
.navlist {
  padding: 15px 0;
  border-top: 4px solid var(--color-black);
  border-bottom: 4px solid var(--color-black);
}
.list_inline{
  min-width: 160px;
  padding: 5px 2.5px;
}
.list_inline:not(:last-child) {
  @media all and (min-width:680px) {
    &:after {
      content: '\A';
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--color-black);
      display: inline-block;
      margin: 0 auto;
    }
  }
  
}

</style>
