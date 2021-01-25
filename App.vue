<template> 
<div> 
<h1> Minhas lista de Tarefas </h1>
<button @click="handleShowHideList"> 
Ver a lista!
</button>
<br> 

<input 
type="text" 
@keyup.enter="addTasks"
v-focus 
v-model="currentTasks"> 

<ul v-if="showList"> 
    <li
    v-for="(task, index) in tasks"
    @dblclick="complete(task)"
    :key="`${task}-${index}`"
    class="task-item"
    :class="{ 
        'line-through': task.isDone    
    }" 

    >
        {{task.name}}

        <button
        @click="remove(task)"
        > &times; </button> 
    </li>
    
</ul>     
<p v-else> Lista de tarefas escondidas </p> 

</div>
</template>

<script> 
const focus  = { 
    inserted: (el) => { 
       el.focus()  
    }
}
export default {
    directives: { 
        focus
    }, 
    
    data: () => ({
        currentTasks: '', 
        showList : false, 
        tasks: [ 
                { name: 'fazendo o curso', isDone: false}
               ]
    }),

   methods: {

       addTasks(){ 
           this.tasks.push({
               name: this.currentTasks, isDone: false
           })
           this.currentTasks = ''
       },

       complete(task) { 
           this.tasks = this.tasks.map(t => { 
                if (t.name ===task.name) { 
                    return {...t, isDone: !t.isDone }
                }
                return { ... t}
           })
       }, 

       handleShowHideList() { 
            this.showList = !this.showList
       }, 

       remove (task) {
           this.tasks = this.tasks.filter( t=>t.name !== task.name)
       
       }
   }
}
</script>

<style scoped>

    .line-through{ 
    text-decoraion: line-through;
    }
    
    .task-item { 
    cursor: pointer;
    }

</style> 

