<script lang="javascript">
  import { store } from '../store.ts'
  import { blur } from 'svelte/transition';

	export let left = 0;
	export let top = 200;

  let height = 5;
  let width = ((1/7) * 100) - 0.5;
	
	let moving = false;
  let resize = false;

	function convertRemToPixels(rem) {    
    return rem * 16; 
  }

  let bottom = top + convertRemToPixels(height);

  let cursorChange = false;
	function onMouseDown(e) {
    let curr = e.clientY;
    if(cursorChange){
      resize = true;
    }
    else if(e.shiftKey){
      removeItem();
    }
    else{
      moving = true;
    }
	}
	
	function onMouseMove(e) {
    if(e.pageY > bottom - 15 && e.pageY <= bottom + 10 && e.clientX >= left &&
    e.clientX <= left + (width*16)){
      cursorChange = true;
    }
    else{
      cursorChange = false;
    }
    if(resize){ 
      if(e.movementY < 0 && height > 2.5){
        height += e.movementY/16
      }
      else if(e.movementY > 0){
        height += e.movementY/16
      }
    }
    else if (moving && !e.shiftKey) {
      left += e.movementX;
      top += e.movementY;        
		}
    bottom = top + convertRemToPixels(height);
	}
	
	function onMouseUp() {
		moving = false;
    resize = false;
	}


  export let objID = {};
  export let color;

  function removeItem(){
    $store = $store.filter((item) => item.id !== objID)
  }	

  function resizeWindow(e){
    console.log(e);
  }
</script>

<section on:mousedown={onMouseDown} style="left: {left}px; top: {top}px;
width:{width}%; height: {height}rem;"
  class="select-none flex absolute
    justify-center items-center resize-y {color} rounded-r-lg"
  class:cursor-move={!cursorChange}
  class:opacity-80={cursorChange}
  class:cursor-row-resize={cursorChange}
  class:drop-shadow-lg={moving}
  
  transition:blur
>
	<slot></slot>
</section>

<svelte:window on:mouseup={onMouseUp} on:mousemove={onMouseMove}
  on:resize={resizeWindow} />

<style lang="postcss"></style>
