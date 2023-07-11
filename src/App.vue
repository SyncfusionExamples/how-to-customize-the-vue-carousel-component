<template>
  <div class="control-container">
    <ejs-carousel ref="Carousel_instance" :dataSource="birdsList" :itemTemplate="'itemTemplate'"
                  :interval="2000" :pauseOnHover="true" :loop="false"
                   :indicatorsTemplate="'indicatorsTemplate'"
                  :previousButtonTemplate="'previousTemplate'"
                  :nextButtonTemplate="'nextTemplate'"
                  
                  :showPlayButton="true"
                  :playButtonTemplate="'playTemplate'"
                  >
           <template v-slot:itemTemplate = "{data}">
              <div>
                <img :src="getImage(data.imageName)" :alt="data.Name"
                      style="height:250px;width:100%;">
                <div><h2>{{ data.Name }}</h2>
                    </div>
              </div>
          </template>
          <template v-slot:indicatorsTemplate="{data}">
            <div class="indicator">
                <img :src="getIndicatorThumbnail(data.index)" alt="image" style="height:3.1rem;width:4.6rem; padding:3px;"/>
            </div>
          </template>
          <template v-slot:previousTemplate>
            <ejs-button cssClass="e-flat e-outline nav-btn">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 40 40" width="40" height="40">
                <path d="m13.5 7.01 13 13m-13 13 13-13"></path>
              </svg>
            </ejs-button>
          </template>
          <template v-slot:nextTemplate>
            <ejs-button cssClass="e-flat e-outline nav-btn">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 40 40" width="40" height="40">
                <path d="m13.5 7.01 13 13m-13 13 13-13"></path>
              </svg>
            </ejs-button>
          </template>
          <template v-slot:playTemplate>
            <ejs-button content="Pause" v-on:click="btnClick"
                        cssClass="e-info playBtn"
                        ref="playBtn"></ejs-button>
          </template>
    </ejs-carousel>
  </div>
</template>

<script>
import { CarouselComponent } from "@syncfusion/ej2-vue-navigations";
import { ButtonComponent } from "@syncfusion/ej2-vue-buttons"
export default {
  components: {
    "ejs-carousel": CarouselComponent,
    "ejs-button": ButtonComponent
  },
  data: function()
  {
    return{
        birdsList:[
        { ID: 1, Name: "Cardinal", imageName: 'cardinal', Content: "Cardinalidae is a family of New World-endemic passerine birds that consists of cardinals, grosbeaks, and buntings. It also includes several birds such as the tanager-like Piranga and the warbler-like Granatellus. As such, membership of this group is not easily defined by a single or even a set of physical characteristics, but instead by molecular work." },
        { ID: 2, Name: "Kingfisher", imageName: 'hunei',Content: "Kingfishers are a family, the Alcedinidae, of small to medium-sized, brightly colored birds in the order Coraciiformes. They have a cosmopolitan distribution, with most species found in the tropical regions of Africa, Asia, and Oceania, but also can be seen in Europe."},
        { ID: 3, Name: "Keel-billed-toucan", imageName: 'costa-rica',Content: "The keel-billed toucan (Ramphastos sulfuratus), also known as sulfur-breasted toucan, keel toucan, or rainbow-billed toucan, is a colorful Latin American member of the toucan family. It is the national bird of Belize. The species is found in tropical jungles from southern Mexico to Colombia."  },
        { ID: 4, Name: "Yellow-warbler", imageName: 'kaohsiung',Content: "Yellow warblers are small widespread songbirds found in the Americas. The summer males of this species are generally the yellowest warblers wherever they occur. They are brilliant yellow below and greenish-golden above. Winter females and immature birds all have similarly greenish-yellow uppersides and are a duller yellow below. "  },
      ],
    };
  },
  methods:
  {
    getImage: function(bird) {
      return "https://ej2.syncfusion.com/products/images/carousel/" + bird + ".png";
    },
    getIndicatorThumbnail: function(index){
      var birds= ["cardinal", "hunei", "costa-rica", "kaohsiung", ];
      return "https://ej2.syncfusion.com/products/images/carousel/" + birds[index] + ".png";
    },
    btnClick: function()
    {
      var carousel_instance=this.$refs.Carousel_instance.ej2Instances;
      var button_instance=this.$refs.playBtn.ej2Instances;
      if(carousel_instance.autoPlay)
      {
        carousel_instance.autoPlay=false;
        button_instance.content="Play";
      }
      else{
        carousel_instance.autoPlay=true;
        button_instance.content="Pause";
      }
     
    }
  } 
 }
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";

.control-container {
 margin: 0 auto 2em;
 max-width: 450px; 
 height: 365px;
} 
.e-carousel-indicators .e-indicator-bars .e-indicator-bar .indicator {
  background-color: #ececec;
  border-radius: 0.25rem;
  cursor: pointer;
  height: 3.5rem;
  margin: 0.5rem;
  width: 5rem;
}
.e-carousel-indicators .e-indicator-bars .e-indicator-bar.e-active .indicator {
  background-color: #3c78ef;
}

.e-carousel-navigators .e-previous
{
  margin-bottom:118px;
  margin-left:-44px;
}
.e-carousel-navigators .e-next
{
  margin-bottom:118px;
  margin-right:-44px;
}

 .e-carousel-navigators .e-previous svg {
  transform: rotate(180deg);
}

 .e-carousel-items,
 .e-carousel-navigators {
  height: calc(100% - 3rem);
}

 .e-carousel-navigators .e-previous,
 .e-carousel-navigators .e-next,
 .e-carousel-navigators .nav-btn {
  padding: 0;
}

 .e-carousel-navigators .nav-btn:active,
 .e-carousel-navigators .nav-btn:focus,
 .e-carousel-navigators .nav-btn:hover {
  background-color: transparent !important;
  color: inherit;
}

 .e-carousel-navigators svg {
  fill: none;
  stroke:currentColor;
  stroke-linecap: square;
  stroke-width: 8px;
  height: 2rem;
  vertical-align: middle;
  width: 2rem;
}

 .e-carousel-navigators .e-previous svg {
  transform: rotate(180deg);
 }
 .e-play-pause
{
  margin-bottom:118px;
} 
</style>