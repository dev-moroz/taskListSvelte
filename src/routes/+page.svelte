<script>
    import "@picocss/pico";
    let newTasks = []
    let completedTasks = []
    let task = ''

    function addTask(){
        const tasks = [...newTasks]

        tasks.push(task)
        newTasks = tasks

        task = ''
    }

    function setComplete(index){
        const completed = [...completedTasks]
        const tasks = [...newTasks]

        completed.push(newTasks[index])
        tasks.splice(index, 1)

        newTasks = tasks
        completedTasks = completed
    }

    function revert(index){
        const completed = [...completedTasks]
        const tasks = [...newTasks]

        tasks.push(completedTasks[index])
        completed.splice(index, 1)

        newTasks = tasks
        completedTasks = completed
    }
    
</script>
<input type="text" bind:value={task}>
<button on:click={addTask}>click</button>
<div>
    <article>
        <h3>newTask</h3>
        {#each newTasks as lol,i (lol)}
        <div>
            <input type="checkbox" key={i} on:click={() => setComplete(i)} />
            <label>{lol}</label>
        </div>
        {/each}
    </article>
</div>

<div>
    <article>
        <h3>Completed</h3>
        {#each completedTasks as lol,i (lol)}
        <div>
            <input type="checkbox" key={i} on:click={() => revert(i)} checked/>
            <label>{lol}</label>
        </div>
        {/each}
    </article>
</div>
