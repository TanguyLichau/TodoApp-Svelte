<script>
  import Todo from "./Todo.svelte";
  export let todolists = [];
</script>

<ul>
  {#each todolists as i}
    <Todo todoValue={i} />
  {/each}
</ul>
