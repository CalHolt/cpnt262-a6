<script>
  import Button from "./Button.svelte";
  // empty string for user input task
  let userInput = "";

  // empty array for all of users inut tasks
  let toDoList = [];

  // create function to allow user to edit ToDo
  function setEditing(i, isEditing) {
    toDoList[i].editing = isEditing;
  }

  // create function to delete ToDo after completing
  function deleteToDo(i) {
    toDoList.splice(i, 1);
    toDoList = toDoList;
  }

  // create function to allow user to add ToDo
  function addToDo () {
    // update to do by making toDoList be every ToDo previously added and add the newly added ToDo
    toDoList = [...toDoList, {content: userInput, editing: false, checked: false}];
  }

  </script>
<main>
<!-- create input area with heading, text input and button to add -->
<div style="margin: 0 auto; padding: 20px; width: 700px;">
  <h1 style="text-align: center;">To Do List</h1>
  <p>Add a Task:</p>
  <div class="input-area">
    <!-- create input box for user input tasks -->
    <input type="text" bind:value={userInput}>
    <!-- button with attached function to add task to list -->
    <Button on:toggle={addToDo} text= "Add"/>
  </div>
</div>

<!-- create display area with checkbox, edit and delete area -->

<!-- Each loop to add more tasks once added -->
{#each toDoList as toDo, i}
<div style="display: flex; align-items: baseline; width: 700px; margin: 0 auto;">
  <!-- create if statement to display text box if user is editing task -->
  {#if toDo.editing}
    <input type="text" bind:value={toDo.content}>
  {:else}
  <input type="checkbox" bind:checked={toDo.checked}>
  <h3 style="flex-grow: 1;">{toDo.content}</h3>
  {/if}
  <div style="display: flex;">
    <!-- Use if statement to show a save button if user is editing a task -->
    {#if toDo.editing}
    <Button on:toggle={() => setEditing(i, false)} text="Save"/>
      <!-- if not editing task show edit button -->
    {:else}
    <Button on:toggle={() => setEditing(i, true)} text="Edit"/>
    {/if}    
    <Button on:toggle={() => deleteToDo(i)} text="Delete"/>
  </div>
</div>
{/each}
</main>
<style>
  input {
    padding: 10px;
    margin-right: 5px;
    border: none;
    background-color:#D0D6B5;
    text-align: center;
  }

  h1 {
    text-decoration: underline;
  }

  .input-area {
    display: flex;
    justify-content: center;
  }

  p {
    text-align: center;
    margin-bottom: 0;
  }

  main {
    color: white;
  }
</style>