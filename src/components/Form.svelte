<script>
    // Form props
    export let name
    export let age
    export let id
    export let action
    export let create

    //functions
    const handleSubmit = (event) => {
        event.preventDefault()
        if(action === 'create'){
            console.log("hello create")
            create({name, age})
        }

        if(action == 'update'){
            console.log('hello update')
        }
    }

</script>

<div>
    <!-- create the form -->
    <form on:submit={handleSubmit}>
        <input type=text bind:value={name}>
        <input type=number bind:value={age}>
        <input type=submit>
    </form>

</div>