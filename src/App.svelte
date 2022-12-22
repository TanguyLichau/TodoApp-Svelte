<script>
  import TodosList from "./TodosList.svelte";
  import Header from "./Header.svelte";
  import AddTodo from "./AddTodo.svelte";
  let todolists = ["a", "b", "c", "d"];

  const whenFavored = (event) => {
    todolists.push(event.detail.value);
    todolists = todolists;
  };
</script>

<Header />
<AddTodo on:favorite={whenFavored} />
<TodosList {todolists} />

<style>
</style>
