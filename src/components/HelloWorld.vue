<template>
  <div class="hello">
    <center>
    <img style="margin-top:-60px" width="100%" src="../assets/gpw1000.jpg"></br></center>
    <div class="tabs is-toggle  is-right">
</div>
<router-link to="/Stock">
<a class="button is-warning is-outlined"  style="margin-left:1180px;margin-top:-800px;font-size:20px">เข้าสู่เว็บไซต์ </a>
 </router-link>
<table class="table is-fullwidth" >
  <tbody v-for =" (stock,key) in showstock"  >
    <tr >
      <td>  <img :src="stock.image"style="width: 100px; height: 100px;"></td>
      <td> </br> </br>{{stock.name}}</td>
      <td> </br></br> {{stock.number}}</td>
      <td> </br></br> {{stock.price}}</td>
   </tr>
      </tbody>
</table>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      showstock: ''
    }
  },
  created: function () {
    this.pullData()
  },
  methods: {
    pullData: function () {
      let that = this
      firebase.database().ref('/stock/').once('value').then(function (snapshot) {
        that.showstock = snapshot.val()
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
