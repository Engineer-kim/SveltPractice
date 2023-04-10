<script>
    import shortid from 'shortid'
    import { todos, saveStorage } from '~/store'
    
    let title = ''
  
    function createTodo() {
      if (!title || !title.trim()) return
      
      $todos.unshift({
        id: shortid.generate(),
        title
      })
      $todos = $todos
      saveStorage()
  
      title = ''
    }
  </script>
   
  <div class="create-todo">
    <input 
      bind:value={title}
      type="text" 
      class="form-control"
      on:keyup={e => {
        if (e.key === 'Enter') createTodo()
      }} />
    <button
      class="btn btn-primary"
      on:click={createTodo}> <!-- 클릭이벤트 등록하는 법은 같지만 svelte 는 약간 다르게  on:click={} 과 같은 방식 이용 -->
      Create Todo!
    </button>
  </div>
  
  <style lang="scss">
    .create-todo {
      margin-top: 50px;
      display: flex;
      .btn {
        width: 130px;
        height: 50px;
        flex-shrink: 0;
        font-weight: 700;
        margin-left: 10px;
      }
    }
  </style>