<script>
    export let tests;

</script>

<div>
    <ul>
        {#each tests as test}
            <li>
                <h3>
                    name: {test.name} 
                    <br/>
                    age: {test.age}
                </h3>
            </li>
        {/each}
    </ul>
    
</div>