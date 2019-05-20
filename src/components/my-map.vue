<template >
<div>
  <div style="text-align: center;">
    <!--  bind the value of url in our data object to the src in our img tag -->
    <img v-bind:src="url">
  </div>

</div>
</template>

<script>


export default {
  name: 'MyMap',
  data(){
    return{
      url : "",
      baseUrl : 'https://maps.googleapis.com/maps/api/staticmap?'
    }
  },
  // props to passed in as a raw value
  props:['latitude','longitude'],

  methods:{
    update:function() {
       this.url = this.baseUrl + 'center=' + this.latitude +',' + this.longitude + '&zoom=17&size=800x800&maptype=roadmap&markers=color:red%7Clabel:%7C'+ 
       this.latitude +',' + this.longitude + '&key=AIzaSyBL-CBfO3UlbqKM6nasJAr6Sf9TGnm6CLQ';
       
    }
  },
  //mount the template to the DOM, essentially meaning 
  //to add the url property to the Vue instance and update the native DOM
  mounted(){
    this.url = this.baseUrl + 'center=' + this.latitude +',' + this.longitude + '&zoom=17&size=800x800&maptype=roadmap&markers=color:red%7Clabel:%7C' + 
    this.latitude +',' + this.longitude + '&key=AIzaSyBL-CBfO3UlbqKM6nasJAr6Sf9TGnm6CLQ';
  }
  }
</script>


