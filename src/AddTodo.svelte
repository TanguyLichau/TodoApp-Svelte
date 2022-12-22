<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let value = "";

  function getTodoValue(event) {
    if (event.key === "Enter") {
      console.log(value);
      dispatch("favorite", { value });
    }
  }
</script>

<div class="input">
  <input
    on:keyup={getTodoValue}
    bind:value
    type="text"
    placeholder="Enter your name"
  />
</div>

<style>
  .input {
    text-align: center;
  }
</style>
