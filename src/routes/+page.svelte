<script>

  let todos = $state([]);

  let todoText  = $state() ;
  let updateState  = $state() ;
  

  const addTodo = () => {
      if(todoText.trim().length>0){
      todos.push({done: false,text: todoText });
    }
    todoText = '';
  }

  const deleteTodo = (index) =>{
    todos.splice(index,1)
  }

  const updateTodo = (index) =>{
    todoText=todos[index].text;
    updateState.focus();
  }
    
    
  
</script>

<h1>Welcome to pukar ojha's shit</h1>


<form onsubmit={(e)=> {e.preventDefault();addTodo()}}>   
  <input type= 'text' bind:this={updateState} bind:value={todoText}/>
  <button>Add</button>
</form>



  <ul>
    {#each todos as todo,index}
      <li>
	<button onclick={()=>{updateTodo(index)}}>u</button>
	<button onclick={()=>{deleteTodo(index)}}>x</button>
	{todo.text}
      </li>

    {/each}
  </ul>



<style>
  :global(body){
  background: #181818;
  color: #FFFFFF;
  width:400px;
  margin: auto;
}
</style>


