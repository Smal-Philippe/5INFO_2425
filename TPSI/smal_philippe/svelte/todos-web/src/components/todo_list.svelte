<script>
    import Icon from "./icon.svelte";
    import Priority from "./priority.svelte";
    import TodoItem from "./todo_item.svelte";

    let todos = []
    let last_id = 0;

    const create_todo = async () => {
        let todo = {
            id: ++last_id,
            task: '',
            done: false,
            priority: 3
        }
        console.log("CREATE: ", todo);
        todos = [...todos, todo]
    }

</script>

<h1>Todos</h1>
<div class="todo-list">
    <div class="header"><Icon nome="tag"/></div>
    <div class="header"><Icon nome="task_alt"/></div>
    <div class="header"><Icon nome="list"/></div>
    <div class="header"><Icon nome="schedule"/></div>
    <div class="header"><Icon nome="add_box" handler={create_todo}/></div>

    {#each todos as todo}
        <TodoItem todo={todo}/>
    {/each}

</div>

<style>
    .todo-list {
        border: 3px solid blue;
        width: 95%;
        height: 80%;
        margin: auto;
        display: grid;
        grid-template-columns: 1fr 1fr 4fr 2fr 1fr;
    }
</style>