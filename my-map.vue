var map = new Vue({
  el: '#map',
  data: {
    lat: 0,
    lon: 0
  }
},
  methods: {
      getLocation: function(event){
          console.log("hi");
      }
  })