<template> 
    <div>
        <h1 :style="{   textDecoration: decoration  }">Hello {{name}}! </h1> 
        <input type="text" v-model="name"> 
        <br> 

        <a :href="link"> Link vuejs </a> 
    </div> 
</template>

<script> 
export default {
    data: () => ({
        name: 'Marcelo', 
        decoration: 'underline',
        link: 'https://cli.vuejs.org/guide/installation.html'
    })
}
</script>
