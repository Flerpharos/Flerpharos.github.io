<script lang="ts">
  import '../app.css';

  let swoosh: HTMLElement;

  const shards: Link[] = [
    {url: '/', text: 'About Me'},
    {url: '/projects', text: 'Projects'},
  ]

  let {children} = $props();
</script>


<div class="absolute bg-zinc-100 dark:bg-emerald-950 inset-0 -z-20 overflow-clip">
  <div class="absolute inset-0 -z-10 pointer-events-none bg-repeat bg-center opacity-10 background-image"></div>
  <div class="swoosh" bind:this={swoosh}></div>
</div>
<!-- <div class="bg-gradient-to-r fixed inset-0 -z-20 from-zinc-800 to-transparent"></div> -->


<div class="shadow-md hover:shadow-emerald-500/20 transition-all shadow-emerald-500/10 bg-zinc-100 dark:bg-emerald-950 w-full relative px-4 overflow-y-auto">
  <div class="absolute inset-0 pointer-events-none bg-repeat bg-center opacity-10 background-image"></div>

  <!-- TODO responsiveness at small sizes -->
  <div class="flex flex-row justify-center">
    {#each shards as shard}
      <a class="nav-button w-max" href={shard.url}>{shard.text}</a>
    {/each}
  </div>
</div>

<div class="w-full h-[calc(100vh-4rem)] z-30 overflow-hidden">
  {@render children()}
</div>


<style>

  .background-image {
    background-image: url('background_lowres.png');
  }

  @media (min-width: 1920px) {
    .background-image {
      background-image: url('background.png');
    }
  }

  .swoosh {
    @apply fixed z-auto -top-64 -left-2/3 w-[200vw] h-96 bg-gradient-to-tl blur-md from-transparent opacity-30 to-transparent via-emerald-600 from-30% to-80% transition-all;
  }

  .nav-button {
    @apply px-6 py-4 text-stone-800 hover:text-emerald-700 focus:text-emerald-700 dark:text-stone-300 dark:hover:text-emerald-300 dark:focus:text-emerald-300 transition-all font-semibold text-xl hover:bg-zinc-300 focus:bg-zinc-300 dark:hover:bg-zinc-900 dark:focus:bg-zinc-900 outline-none
  }

</style>