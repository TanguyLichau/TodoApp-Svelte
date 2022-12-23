<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  function checkAllTodos() {
    dispatch("checkAll");
  }

  function deleteAllTodosDone() {
    dispatch("deleteAll");
  }
</script>

<div id="buttons">
  <button on:click={checkAllTodos}>Check all</button>
  <button on:click={deleteAllTodosDone}>Delete done</button>
</div>

<style>
  #buttons {
    margin-top: 45px;
    text-align: center;
  }
</style>
