<template>
<div class="content-wrapper">
  <div id="hero" class="hero-wrapper">

    <!-- <div class="PH-badge">
      <Sponsor class="gitHub-sponsor"/>
    </div> -->
    <div class="hero-text-area" v-if="iconsEmpty">    
        
        <p class="coral-Body--S desktop-hidden">
          Hosting by
          <a href="https://fosshost.org/" rel="noopener" target="_blank" class="coral-Link">
              FossHost
          </a> 
        </p>

        <h3
          class="main-heading m-t-0 coral-Heading--XL coral-Heading--regular"
        >
          <span class="f-w-100 f-s-26">macOS Big Sur</span>
          <br />
          Replacement Icons
        </h3>

        <p class="coral-Body--L w-100 body-text">
            Sponsor the project on
          <a rel="noopener" class="coral-Link" href="https://github.com/sponsors/elrumo">
            GitHub
          </a>
            and follow its develoment on 
          <a rel="noopener"
            class="coral-Link"
            href="https://twitter.com/elrumo"
            target="_blank"
          >
            <b>Twitter.</b>
          </a>
          
          Templates to contribute:
          <a rel="noopener"
            class="coral-Link"
            href="https://github.com/elrumo/macOS_Big_Sur_icons_replacements/raw/master/design/Template-Icon-App.sketch"
            alt="Sketch template"
            @click="updateCount('cftvIOYXek')"
          >
          <!-- <a rel="noopener"
            class="coral-Link"
            href="https://github.com/elrumo/macOS_Big_Sur_icons_replacements/raw/master/design/Template-Icon-App.sketch"
            @click="updateCount('cftvIOYXek')"
          > -->
            Sketch,
          </a>
          <a rel="noopener"
            class="coral-Link"
            href="https://www.figma.com/community/file/930870327989917713/MacOS-Big-Sur-icon-template"
            alt="Figma template"
            @click="updateCount('ecCJEYIUyF')"
          >
            Figma,
          </a>
          <a rel="noopener"
            class="coral-Link"
            alt="Illustrator template"
            href="https://github.com/elrumo/macOS_Big_Sur_icons_replacements/raw/master/design/Template-Icon-App.ai"
            @click="updateCount('fu7UfKs2zz')"
          >
            Illustrator,
          </a>
          or
          <a rel="noopener"
            class="coral-Link"
            alt="Photoshop template"
            href="https://github.com/elrumo/macOS_Big_Sur_icons_replacements/raw/master/design/Template-Icon-App.psd"
          >
            Photoshop.
          </a>
        </p>

        <div class="m-auto m-t-35">
          <div class="d-inline-block">
            <button
              is="coral-button"
              variant="cta"
              @click="showDialog(submitIconDialog)"
            >
              <span>Submit icons</span>
            </button>
          </div>

            <!-- href="https://ko-fi.com/I3I63CFCN" -->
            <!-- href="https://www.buymeacoffee.com/elrumo" -->
          <!-- <a rel="noopener"
            class="p-l-20 mobile-hidden"
            target="_blank"
            href="https://www.paypal.com/donate/?hosted_button_id=5PMNX4DPW83KN"
          >
            <button is="coral-button" variant="quiet">
              <span>Buy me a coffee</span>
            </button>
          </a> -->
              <!-- <span>☕️ Buy me a hot chocolate</span> -->
              <!-- <span>Help keep this site alive</span> -->
              <!-- <span class="p-r-5 f-s-16">☕️</span> <span>Buy me a hot chocolate</span> -->
          
        </div>
    </div>
    
    <img class="hero-img mobile-hidden" :src="imgs.heroImg" alt="">

  </div>
</div>
</template>

<script>
import Sponsor from "./Sponsor.vue";

export default {
  name: "Hero",

  components:{
    Sponsor
  },

  data() {
    return {
      imgs:{
        heroImg: require("../assets/icons_hero.jpg")
      }
    };
  },

  props: {
    list: {},
    submitIconDialog: String,
    iconListLen: 0,
    iconsEmpty: Boolean,
    parseObj: {},
  },

  methods: {

    async updateCount(id){
      let parent = this;

      let Icons = await parent.parseObj

      let query = new Icons.Query(Icons)
      let docToUpdate = await query.get(id)

      docToUpdate.increment("downloads")
      docToUpdate.save().then(() => {
        console.log("Saved!!");
      }).catch((e) => {
        console.log("error: ", e);
      })
    },

    showDialog(dialog) {
      let dialogEl = document.getElementById(dialog);
      dialogEl.show();
    },

    goToSponsor() {
      window.open("https://github.com/sponsors/elrumo?o=esc", "_blank");
    },
  },

  mounted: function() {},

  computed: {
  }

};
</script>

<style>
</style>
