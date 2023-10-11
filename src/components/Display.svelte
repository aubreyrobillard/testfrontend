<script>
    export let tests;
    export let select;

</script>

<div>
    <ul>
        {#each tests as test}
            <li>
                <button on:click={() => select(test)}> name: {test.name} age: {test.age} </button>
            </li>
        {/each}
    </ul>
    
</div>