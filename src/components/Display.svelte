<script>
    export let tests;
    export let select;
    export let destroy

</script>

<div>
    <ul>
        {#each tests as test}
            <li>
                <button on:click={() => select(test)}> name: {test.name} age: {test.age} </button>
                <button on:click={() => {destroy(test)}}>Delete</button>
            </li>
        {/each}
    </ul>
    
</div>