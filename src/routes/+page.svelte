<script>
  import Block from '../components/block.svelte'
  import Headers from '../components/headers.svelte'
  import Event from '../components/event.svelte'

  import { store, id } from '../store.ts'

  let currX, currY;
  $store = []

  let title = ""
  let colorOptions = ["bg-emerald-300", "bg-sky-300", "bg-red-300",
  "bg-indigo-300", "bg-pink-300", "bg-yellow-300"];

  id.set(0);

  function addEvent(){
    let len = $store.length;
    
    $store[len] = {id: $id, name:title, color: colorOptions[Math.floor(Math.random() * 6)]};
    title = "";
    $id++;
  }

  function clearEvents(){
    $store = [];
  }
</script>

<div class="mr-2 flex gap-3 justify-end items-end">
  <a href="/">archive</a>
  <a href="/">settings</a>
</div>

<div class="flex flex-col mr-2 justify-start items-end">
  <button class="text-red-500" on:click={clearEvents}>
    clear events
  </button>
</div>


<Headers/>
<div class="flex mb-2 h-screen box-border">
  <div class="grid grid-cols-1 ml-2 absolute z-40">
    {#each Array(16) as _, i (i)}
      <h1 class="text-sm h-20 pl-1">{7+i}</h1>
    {/each}
  </div>
  <div class="h-fit w-full ml-2 mr-2 pb-2 grid grid-cols-7">

    {#each $store as item}
      <Event left={item.left} top={item.top} color={item.color} objID={item.id}>
          <h4 class="text-sm">{item.name}</h4>
        </Event>
    {/each}

    {#each Array(16) as _, i (i)}
      {#each Array(7) as _, j (j)}
        <Block row={i} col={j}/>
      {/each}
    {/each}

  </div>
</div>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.slate.50);
  }
</style>

<!-- <svelte:body on:mousedown={onMouseDown}/> -->
