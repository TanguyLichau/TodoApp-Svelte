<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let todoValue = "";
  export let indx;
  export let isChecked = false;

  function checkTodo() {
    isChecked = !isChecked;
    dispatch("check");
  }
  function deleteTodo() {
    dispatch("delete", { todoIndex: indx });
  }
</script>

<div>
  {#if isChecked}
    <p class="checked">{todoValue}</p>
  {:else}
    <p class="notchecked">{todoValue}</p>
  {/if}
  <button on:click={checkTodo}> check</button>
  <button on:click={deleteTodo}> destroy</button>
</div>

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
