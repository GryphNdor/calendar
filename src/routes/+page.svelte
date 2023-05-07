<script>
  import Block from '../components/block.svelte'
  import Headers from '../components/headers.svelte'
  import Event from '../components/event.svelte'

  import { writable } from 'svelte/store';

  let store = writable({});

  let currX, currY;

  function onMouseDown(e){
    currX = event.clientX;
    currY = event.clientY;
  }

  $store = []

  let title = ""
  let colorOptions = ["bg-emerald-300", "bg-sky-300", "bg-red-300",
  "bg-indigo-300", "bg-pink-300", "bg-yellow-300"];
  function addEvent(){
    let len = $store.length;
    
    $store[len] = {name:title, color: colorOptions[Math.floor(Math.random() * 6)]};
    title = "";
  }

  function clearEvents(){
    $store = [];
  }
</script>

<div class="mr-2 flex gap-3 justify-end items-end">
  <a href="/">archive</a>
  <a href="/">settings</a>
</div>

<div class="flex flex-col justify-start items-center">
  <input class="mt-1 px-3 py-2 bg-white border shadow-sm border-slate-300
    placeholder-slate-400 focus:outline-none focus:border-sky-500
    focus:ring-sky-500 block w-48 rounded-md sm:text-sm focus:ring-1"
    bind:value={title}/>
  <button class="hover:text-emerald-400" on:click={addEvent}>
    add new event
  </button>
  <button class="text-red-500" on:click={clearEvents}>
    clear events
  </button>
</div>

<Headers/>

<div class="ml-2 mr-2 h-screen box-border">
  <div class="h-fit mb-2 grid grid-cols-7">

  {#each $store as item}
      <Event left={currX} top={currY} color={item.color}>{item.name}</Event>
  {/each}
    <Block row={0} col={0}/>
    <Block row={0} col={1}/>
    <Block row={0} col={2}/>
    <Block row={0} col={3}/>
    <Block row={0} col={4}/>
    <Block row={0} col={5}/>
    <Block row={0} col={6}/>

    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>

    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>

    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>

    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>

    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>

    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>

    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>

    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>

    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>
    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>
    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>
    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>
    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>
    <Block row={1} col={0}/>
    <Block row={1} col={1}/>
    <Block row={1} col={2}/>
    <Block row={1} col={3}/>
    <Block row={1} col={4}/>
    <Block row={1} col={5}/>
    <Block row={1} col={6}/>
  </div>
</div>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.slate.50);
  }
</style>

<!-- <svelte:body on:mousedown={onMouseDown}/> -->
