<template id="add-post">
  <div>
    <h3>Add new Post</h3>
    <form v-on:submit.prevent = "createPost">
      <div class="form-group">
        <label for="add-title">Title</label>
        <input id="add-title" v-model="post.title" class="form-control" required />
      </div>
      <div class="form-group">
        <label for="add-body">Body</label>
        <textarea class="form-control" rows="10" v-model="post.body"></textarea>
      </div>
      <button type="submit" class="btn btn-xs btn-primary">Create Post</button>
      <router-link class="btn btn-xs btn-warning" v-bind:to="'/'">Cancel</router-link>
    </form>
  </div>
</template>
<script type="text/javascript">
  
  export default{

    data: function(){
     return{post:{title: '' ,body:''}}

    },
    methods:{
      createPost:function(){
        Axios.post('/posts/',this.post).then((res)=>{
          this.$router.push({name:'Listposts'})
        })
      }
    }
  }
</script>