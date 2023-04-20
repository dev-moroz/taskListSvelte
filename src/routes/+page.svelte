<script>
    import "@picocss/pico";
    let newTasks = ['1']
    let completedTasks = []
    let task = ''

    function addTask(){
        newTasks.push(task)
        newTasks = newTasks        
        task = ''
    }

    function setComplet(index){
        completedTasks.push(newTasks[index])
        completedTasks = completedTasks
        newTasks.splice(index, 1)
        newTasks = newTasks
    }

    function revert(index){
        newTasks.push(completedTasks[index])
        newTasks = newTasks
        completedTasks.splice(index, 1)
        completedTasks = completedTasks
    }
</script>
<input type="text" bind:value={task}>
<button on:click={addTask}>click</button>
<div>
    <article>
        <h3>newTask</h3>
        {#each newTasks as lol,i (lol)}
        <div>
            <input type="checkbox" key={i} on:click={() => setComplet(i)} />
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
