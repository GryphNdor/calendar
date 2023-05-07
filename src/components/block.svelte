<script>
  import {onMount} from 'svelte'
  export let row;
  export let col;
  export let bounding;
  let blockID = crypto.randomUUID();

  import { store, id } from '../store.ts'

  let title = ""
  let colorOptions = ["bg-emerald-300", "bg-sky-300", "bg-red-300",
  "bg-indigo-300", "bg-pink-300", "bg-yellow-300"];

  function addEvent(){
    let len = $store.length;
    $store[len] = {id: $id, blockID,left:bounding.left,top:bounding.top, name:title, color: colorOptions[Math.floor(Math.random() * 6)]};
    title = "";
    $id++;
  }


  let rect;
  onMount(() => {
    bounding = rect.getBoundingClientRect();
  });

  function updateBouding(){
    bounding = rect.getBoundingClientRect();
    for(let i = 0; i < $store.length; i++){
      if($store[i].blockID === blockID){
       $store[i].left = bounding.left;
       $store[i].top = bounding.top;
      }
    }
  }
</script>

{#if row === 0 && col === 0}
  <div on:mousedown={addEvent} bind:this={rect} class="flex  h-20 border border-black center-items">
    <div class="w-full h-1/2 border-b border-black border-dotted">
    </div>
  </div>
{:else if row === 0}
  <div on:mousedown={addEvent} bind:this={rect} class="flex  h-20 border-b border-t border-r border-black justify-center center-items">
    <div class="w-full h-1/2 border-b border-black border-dotted"></div>
  </div>
{:else if col === 6}
  <div on:mousedown={addEvent} bind:this={rect} class="flex h-20 border-b border-r border-black center-items">
    <div class="w-full h-1/2 border-b border-black border-dotted">
    </div>
  </div>
{:else if col === 0}
  <div on:mousedown={addEvent} bind:this={rect} class="flex h-20 border-b border-l border-r border-black center-items">
    <div class="w-full h-1/2 border-b border-black border-dotted">
    </div>
  </div>
{:else}
  <div on:mousedown={addEvent} bind:this={rect} class="flex h-20 border-b border-r border-black center-items">
    <div class="w-full h-1/2 border-b border-black border-dotted"></div>
  </div>
{/if}

<style lang="postcss">
</style>

<svelte:window on:resize={updateBouding}/>
