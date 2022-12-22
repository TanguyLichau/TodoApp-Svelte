<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let value = "";

  function getTodoValue(event) {
    if (event.key === "Enter") {
      dispatch("add", { value });
      const todoInput = (document.getElementById("inp").value = "");
    }
  }
</script>

<div class="input">
  <input
    id="inp"
    on:keyup={getTodoValue}
    bind:value
    type="text"
    placeholder="Add a task.."
  />
</div>

<style>
  .input {
    text-align: center;
  }
</style>
