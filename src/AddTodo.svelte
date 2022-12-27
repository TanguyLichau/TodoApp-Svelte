<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let obj = {
    todoValue: null,
    index: null,
    isChecked: false,
  };

  function getTodoValue(event) {
    if (event.key === "Enter") {
      obj.todoValue = document.getElementById("inp").value;
      dispatch("add", obj);
      const todoInput = (document.getElementById("inp").value = "");
    }
  }
</script>

<div class="input">
  <input
    id="inp"
    on:keyup={getTodoValue}
    type="text"
    placeholder="Add a task.."
  />
</div>

<style>
  .input {
    text-align: center;
  }
</style>
