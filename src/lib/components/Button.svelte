<script>
  // import event dispatcher
  import { createEventDispatcher } from "svelte";
  // create variable for event dispatcher MAKE SURE TO PUT () AFTER CREATEEVENTDISPATCHER
  const dispatch = createEventDispatcher();
  // Create function calling variable made for event dispatcher
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