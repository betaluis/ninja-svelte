<script>
  import { createEventDispatcher } from 'svelte';
  let dispatcher = createEventDispatcher();
  // your script goes here
  export let todos = []; 

  // Just because you're referecing a handler inside of a loop doesn't mean you have access to the item when using an handler.
  // const handler = () => { console.log(todos) } ========> This would not work. "Todos" will be undefined

  // You can't pass in todos as an argument to the handler because it will envoke the function each time.
  
  // The way you go about this is creating an inline function.

  const handleClick = (id) => {
    todos = todos.filter(t => id !== t.id);
    dispatcher("updatedTodoList", todos);
  }

</script>

<section>
  <ul>
  {#each todos as todo (todo.id)}
    <div class="flex">
      <li on:click={() => handleClick(todo.id)}>{todo.task}</li>
      <button on:click={() => handleClick(todo.id)}>Delete</button>
    </div>
  {:else}
    <p>You're all caught up. Add more todos if anything comes up.</p>
  {/each}
  </ul>
</section>

<style>
  li {
    list-style: none;
    padding: 10px 0;
    background-color: dodgerblue;
    color: white;
    cursor: pointer;
    flex: 1;
  }
  button {
    background-color: none;
    padding: 10px 12px;
    margin: 0;
    justify-self: center;
    cursor: pointer;
  }
  .flex {
    display: flex;
    width: 100%;
    gap: 10px;
    align-items: center;
    margin: 10px auto;
    max-width: 600px;
  }
</style>
