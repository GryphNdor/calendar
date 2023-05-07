<script lang="javascript">
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
    else{
      moving = true;
    }
    
	}
	
	function onMouseMove(e) {
    if(e.clientY > bottom - 15 && e.clientY <= bottom + 10){
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
    else if (moving) {
      left += e.movementX;
      top += e.movementY;        
		}
    bottom = top + convertRemToPixels(height);
	}
	
	function onMouseUp() {
		moving = false;
    resize = false;
	}


  export let color="bg-emerald-500"
	
// 	$: console.log(moving);
</script>

{#if cursorChange === false}
<section on:mousedown={onMouseDown} style="left: {left}px; top: {top}px;
width:{width}%; height: {height}rem;"
  class="cursor-move select-none flex absolute
    justify-center items-center resize-y {color}">
	<slot></slot>
</section>
{:else}
<section on:mousedown={onMouseDown} style="left: {left}px; top: {top}px;
width:{width}%; height: {height}rem"
  class="cursor-row-resize select-none flex absolute
    justify-center items-center resize-y {color}"
    class:color={color}>
	<slot></slot>
</section>
{/if}

<svelte:window on:mouseup={onMouseUp} on:mousemove={onMouseMove} />

<style lang="postcss">
</style>
