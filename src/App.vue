
<template>
<div id = "app">
    <div class="container">
        <div class="jumbotron">
            <h4 class="display-4">
                 {{msg}}
            </h4>
            <p class="lead">Enter your latitude and longitude to display your location on a Google Map</p>
            <hr>
            <form v-on:submit.prevent="getLocation">
                <div class="form-row">
                    <div class="col">
                        <input type="text" name="lat" id="lat" placeholder="Latitude" required v-model="input.lat" class="form-control" >
                    </div>
                    <div class="col">
                        <input type="text" name="lon" id="lon" placeholder="Longitude" required v-model="input.lon" class="form-control">
                    </div>
                </div>
                <div class="form-row">
                    <div class="col">
                        <input type="submit" value="Show My Location" class="btn btn-primary mt-4">
                    </div>
                </div>
            </form>
        </div>
    </div>
    <div>
      <img class="img-fluid shadow-lg p-3 mb-5 bg-white rounded"  v-bind:src="img"/> <br><br><br><br>
    </div>
</div>

</template>

<script>
    const apiKey = 'AIzaSyA0zfP5tU-Drqkijz6uoKqyc1cwQ64i60Q';
    export default {
        name: 'app',        
        data () {
            return {
              msg: 'My Location',
              input: {
               lat: '',
               lon: ''
            },
            img: ''
            }
        },
        methods: {
            getLocation () {
                console.log(this.input.lat)
                console.log(this.input.lon)
                this.img = `https://maps.googleapis.com/maps/api/staticmap?center=${this.input.lat},${this.input.lon}&zoom=13&size=600x600&markers=${this.input.lat},${this.input.lon}&key=${apiKey}`
                console.log(this.img)
            }
        }
        
        
    }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  h1,
  h2 {
    font-weight: normal;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
