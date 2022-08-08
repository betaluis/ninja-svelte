<script>
    import { createEventDispatcher } from 'svelte'
    let dispatcher = createEventDispatcher();

    let todo;
    const handleSubmit = () => {
        const newTodo = {
            task: todo,
            id: Math.floor(Math.random() * 1000),
        }
        dispatcher('addTodo', newTodo);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <h3>Add Todo</h3>
    <input type="text" placeholder="Enter a new todo" bind:value={todo}>
    <button type="submit">Add todo</button>
</form>