<template id="post">
  <div>
    <h3>{{ post.title }}</h3>
    <strong>Body : </strong>
    <div>
      {{ post.body }}
    </div>
  </br>
  <span class="glyphicon glyphicon-arrow-left"></span>
  <router-link v-bind:to="'/'">Back to post list</router-link>
  </div>
</template>

<script>
   export default {
   data: function () {
   return {post: {title: '', body: ''}}
 },
 created: function(){
let url = window.location.href;
let pageNumber = url.replace('view','posts');

//alert(pageNumber)
  // let uri = pageNumber+this.$route.params.id;
     Axios.get(pageNumber).then((response) => {
        console.log(response.data)
     this.post = response.data;
   });
 }
 }
</script>