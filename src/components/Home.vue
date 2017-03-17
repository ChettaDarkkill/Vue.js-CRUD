<template>
<div>
  <div class="col-sm-6 col-md-4" v-for="item in list">
  <div class="thumbnail">
  <img :src="item.url" :alt="item.title">
  <div class="caption">
     <h3>{{ item.title }}</h3>
  </div>
  <button type="button" class="btn btn-default" aria-label="Left Align">
  <span class="glyphicon glyphicon-align-left" aria-hidden="true"></span>
</button>
  </div>
  </div>
</div>
</template>

<script>

export default {
  name: 'Home',
  data () {
    return {
      list: []
    }
  },
  created: function () {
    this.$http.get('http://localhost:5000/photos/')
    .then(response => {
      this.list = response.body
    }, response => {
      this.list = []
    })
  }
}
</script>
