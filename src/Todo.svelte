<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let todoValue = "";
  export let indx;
  export let isChecked = false;
  let editing = false;

  function checkTodo() {
    isChecked = !isChecked;
    dispatch("check");
  }
  function deleteTodo() {
    dispatch("delete", { todoIndex: indx });
  }
  function editTodo() {
    editing = true;
  }
  function saveEdit() {
    editing = false;
  }
</script>

{#if editing}
  <div>
    <input id="edit" type="text" bind:value={todoValue} />
    <button on:click={saveEdit}>Save</button>
  </div>
{:else}
  <div>
    {#if isChecked}
      <p class="checked">{todoValue}</p>
    {:else}
      <p class="notchecked">{todoValue}</p>
    {/if}
    <button on:click={checkTodo}> check</button>
    <button on:click={deleteTodo}> destroy</button>
    <button on:click={editTodo}> edit</button>
  </div>
{/if}

<style>
  .checked {
    text-decoration: line-through;
  }
  p {
    display: inline-block;
    margin-right: 30px;
  }
  div {
    text-align: center;
  }
</style>
