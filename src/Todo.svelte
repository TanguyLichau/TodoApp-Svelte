<script>
  export let todoValue = "";
  let todo = {
    text: todoValue,
    isChecked: false,
  };

  function checkTodo() {
    todo.isChecked = !todo.isChecked;
  }
</script>

<div>
  {#if todo.isChecked}
    <p class="checked">{todo.text}</p>
  {:else}
    <p class="notchecked">{todo.text}</p>
  {/if}
  <button on:click={checkTodo}> check</button>
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
