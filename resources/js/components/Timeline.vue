<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card card-default">
                    <div class="card-header">Timeline</div>
                    
                    <div class="card-body">
                      <post-tweet></post-tweet>
                       <div class="media" v-for="tweet in tweets">
                          <div class="media-left">
                             
                          </div>
                          <div class="media-body" id="app">
                             <strong>{{ tweet.user.name }}</strong>
                             <p>{{ tweet.body }}</p>
                             
                          </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    </div>
</template>

<script>
    import PostTweet from './PostTweet.vue'

    export default { 
       data(){
          return{
            tweets:[],
             tweet:{
               id: '',
               user:'',
               body:'',
             }
          }
       },        

       mounted(){
           this.getTweets()
       },
       methods:{
          getTweets(){
              axios.get('/tweets').then(response =>{
                  
                  this.tweets = response.data
              });
          }
       }
    }
</script>

