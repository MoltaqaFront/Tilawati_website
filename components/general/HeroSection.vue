<template>
  <div id="hero_section" class="hero_section_wrapper">
    <!-- Start:: Section Content -->
    <div class="slider_image_wrapper">
      <div class="slide_content_wrapper">
        <div class="container-xl">

          <div class="slide_desc_content_wrapper">
            <div class="accordion" role="tablist">

              <div class="cards">
                <!-- @click="scrollToSection('define_quran')" -->
                <div class="card-header">
                  <span v-html="headerText"></span>
                </div>
              </div>

            </div>
          </div>

        </div>
      </div>
    </div>
    <!-- End:: Section Content -->

    <!-- Start:: Mobile Mockup -->
    <div class="mobile_mockup_wrapper focus_screen" data-aos-once="true" data-aos="zoom-in" data-aos-delay="500"
      data-aos-duration="1000">
      <!-- <client-only>
        <nuxt-img
          provider="static"
          src="~/assets/media/images/mobileScreens/logoScreen.png"
          alt="App Splash"
          format="webp"
          width="450"
          height="300"
          quality="100"
          loading="lazy"
        />
      </client-only> -->
      <img src="~/assets/media/images/mobileScreens/hero_2.png" width="450" height="300" alt="App Splash"
        loading="lazy" />
    </div>
    <!-- End:: Mobile Mockup -->
  </div>
</template>

<script>
export default {
  name: "HeroSection",

  data() {
    return {
      isLoading: false,
      questions: []
    }
  },

  computed: {
    headerText() {
      return this.$store.state.headerText
    }
  },

  methods: {

    // START:: SCROLL TO SECTION
    scrollToSection(section_id) {
      if (this.$route.path != this.localePath('/')) {
        this.$router.push(this.localePath('/'))
      } else {
        const selected_section = document.querySelector(`#${section_id}`)
        selected_section.scrollIntoView({ behavior: 'smooth', block: 'start', inline: 'nearest', offsetTop: -50 });
      }
    },
    // END:: SCROLL TO SECTION

    async getData() {
      try {
        return await this.$axios.get(`questions`).then(response => {
          this.isLoading = true;
          this.questions = response.data.data;
        }).catch(error => {
          console.log(error)
        })
      } catch (error) {
        console.log("catch : " + error)
      }
    }
  },

  mounted() {
    this.getData();
    setTimeout(() => {
      this.isLoading = false;
      document.body.style.overflow = "unset";
    }, 2000);
  }
};
</script>

<style>
.accordion {
  box-shadow: 0 0px 16px #b97e12;
  border-radius: 5px;
  background: #000;
  padding: 20px 30px;
  margin-top: 40px;
}

.card-header {
  background: #000;
  /* padding: 10px; */
  /* text-align: center; */
  color: #b97e12;
  /* border: 1px solid #FFF; */
  border-radius: 5px;
  cursor: pointer
}

p {
  font-size: 17px
}

.btn-secondary {
  color: #b97e12;
  background: #000;
  width: 100%;
  border: none;
  outline: none
}

ul li {
  list-style: auto
}
</style>
