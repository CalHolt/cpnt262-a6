<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  function click() {
		dispatch('toggle', {});
	}
 export let text; 
</script>

<button on:click={click}>{text}</button>

<style>
  button {
    background-color: #987284;
    color: white;
    padding: 5px;
  }
  button:hover {
    cursor: pointer;
    background-color: #386939;
  }
</style>