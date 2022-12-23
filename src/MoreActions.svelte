<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let checkedAll = true;

  function checkAllTodos() {
    dispatch("checkAll");
    checkedAll = !checkedAll;
  }

  function deleteAllTodosDone() {
    dispatch("deleteAll");
  }
</script>

<div id="buttons">
  <button on:click={checkAllTodos}
    >{checkedAll ? "Check all" : "Uncheck All"}</button
  >
  <button on:click={deleteAllTodosDone}>Delete done</button>
</div>

<style>
  #buttons {
    margin-top: 45px;
    text-align: center;
  }
</style>
