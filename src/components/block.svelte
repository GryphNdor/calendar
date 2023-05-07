<script>
  export let row;
  export let col;
</script>

{#if row === 0 && col === 6}
  <div class="flex h-20 border border-black center-items">
    <div class="w-full h-1/2 border-b border-black border-dotted"></div>
  </div>
{:else if row === 0}
  <div class="flex h-20 border-b border-t border-l border-black center-items">
    <div class="w-full h-1/2 border-b border-black border-dotted"></div>
  </div>
{:else if col === 6}
  <div class="flex h-20 border-b border-l border-r border-black center-items">
    <div class="w-full h-1/2 border-b border-black border-dotted"></div>
  </div>
{:else}
  <div class="flex h-20 border-b border-l border-black center-items">
    <div class="w-full h-1/2 border-b border-black border-dotted"></div>
  </div>
{/if}

<style lang="postcss">
</style>
