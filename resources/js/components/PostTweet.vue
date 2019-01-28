<template>
    <form action="#">
       <div class="form-group">
          <textarea class="form-group" cols="50" rows="2" v-model="body"></textarea>
          <br>
          <button class="btn btn-success" type="button" v-on:click="addPost()">Post</button>
       </div>
    </form>
</template>

<script>
    export default{
         data(){

         return {
            body:'',
         }

       },
       props:[
	       'tweets'
	       ],
   
    methods:{
	    addPost(){       

	       axios.post('/tweets',{
	          body: this.body,
	       }).then(response => {
	            window.location = "/home"
	       }).catch(error => {
	            console.log(error)
	       })
	    }
    }
  }
</script>