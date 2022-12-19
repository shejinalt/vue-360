<template>
  <div id="app">
    <div class="container">
      <div class="row">

        <!-- Example 1 - Car -->
        <div class="col-12 mb-4 card p-0">
          <vue-three-sixty
            :amount=36
            imagePath="https://scaleflex.cloudimg.io/v7/demo/suv-orange-car-360"
            fileName="orange-{index}.jpg"
            spinReverse
            buttonClass="dark"
            scrollImage

            @hotWidget="hotWidget"
            :hotspots=myHotspots



          >

            <template v-slot:header>
              <div class="v360-header text-light bg-dark">
                  <span class="v360-header-title">36 Images - Autoplay (1 loop) - Reverse Spin</span>
                  <span class="v360-header-description"></span>
              </div>
            </template>

          </vue-three-sixty>
        </div>
        <!--/ Example 1 - Car -->



      </div>
    </div>
  </div>
</template>

<script>

//import I360Viewer from './components/I360Viewer.vue'

export default {
  name: 'app',

  props: {

  },
  data() {
        return {

            myHotspots:[{
                id: 2,
                frame : 2,
                text:"this is hotspot",
                x: 400,
                y:300,

                //icon:"https://icon-library.com/images/icon-p/icon-p-15.jpg",
                // action: function hotWidget(params) {
                //   console.log("xx");
                // }

            }],

        }
    },
  mounted() {
    //safari zoom bug fix
    this.disableZoomin();
  },

  methods: {
    disableZoomin(){
      document.addEventListener("gesturestart", function (e) {
        e.preventDefault();
          document.body.style.zoom = 0.99;
      });
      document.addEventListener("gesturechange", function (e) {
        e.preventDefault();
        document.body.style.zoom = 0.99;
      });

      document.addEventListener("gestureend", function (e) {
          e.preventDefault();
          document.body.style.zoom = 1;
      });
    },
    hotWidget(id){
      console.log(id,"trigger from app");
    },

    //
  }
}
</script>
