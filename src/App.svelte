<script>
  import {onMount} from 'svelte'
  import Display from "./components/Display.svelte";
  import Form from "./components/Form.svelte";

  
  const url = 'https://testbackend-ep12.onrender.com/test/'

  //state
  let showForm = false
  let id = ""
  let name = ""
  let age = ""
  let action = 'create'
  //state to hold tests
  let tests = []

////////////////////////////////////////////////////////////////////////

  //Index function
  // index data stored in "tests"
  const getTests = async () => {
    const response = await fetch(url)
    const data = await response.json()
    tests = data
  }

  // view and hide create form function
  const toggleForm = () => {
    showForm = !showForm
  }

  // Reset state function
  const resetState = () => {
    showForm = false
    id = ""
    name = ""
    age = ""
    action = 'create'
  }

  //Create Function
  const createTest = async (test) => {
    await fetch(url, {
      method: 'post',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify(test)
    })
    getTests()
    resetState()
  }

  //lifecycle
  onMount(() => {getTests()})

</script>


<main>
  <h1>Aubrey's Test Project</h1>
  
  <button on:click={toggleForm}>Create a Test</button>
  
  <!-- display is done through getTests() in app, tests prop & mapping in display.  -->
  <!-- filling the tests state with the tests fetched from getTests() -->
  <Display tests={tests}/>
  
  {#if showForm}
    <Form
      name={name}
      age={age}
      id={id}
      action={action}
      create={createTest}
    />
  {/if}

</main>






<style>
  
</style>
