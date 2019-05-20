<template lang= html>
 <html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    <title>CS4220 Final</title>
</head>
<body>
    <div class="container">
        <div class="jumbotron">
            <h4 class="display-4">
                My Location
            </h4>
            
            <p class="lead">Enter your latitude and longitude to display your location on a Google Map</p>
            <hr>
        
                <div class="form-row">
                    <div class="col">
                        <!-- take in the latitude from user-->
                        <input type="text" name="lat" id="lat" placeholder="Latitude" class="form-control" v-model="latitude">
                    </div>
                    <div class="col">
                        <!-- take in the longitude from user-->
                        <input type="text" name="lon" id="lon" placeholder="Longitude" class="form-control" v-model="longitude">
                    </div>
                    
                </div>
                <div class="form-row">
                    <div class="col">
                        <!-- on click call onSubmit function-->
                        <input type="submit" @click="onSubmit" value="Show My Location" class="btn btn-primary mt-4" >
                    </div>
                </div>
           
        </div>
            <!-- if submit is true set the latitude and longitude giving by the user -->
            <my-map v-if="submit" ref="location" :latitude="latitude" :longitude="longitude"></my-map>
    </div>
</body>
</html>
</template>

<script>

import MyMap from './components/my-map.vue'

export default {
// instance  
  name: 'app',
  data(){
      return{
          submit:false,
          latitude:'',
          longitude:'',
          query_param:""
      }
  },
  components: {
    MyMap
  },
  methods:{
      onSubmit(){
        if(this.submit){
            // reference to the submit  and call the update function
          this.$refs.location.update();
          
        } 
        this.submit = true;
      },
    
  }
}
</script>


