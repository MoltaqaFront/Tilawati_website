<template>
  <div id="about_section" class="about_section_content_wrapper">
    <div class="container">
      <div class="row align-items-center px-5">
        <div class="accordion" id="accordionExample">
          <div class="accordion-item">
            <h2 class="accordion-header" id="headingOne">
              <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne"
                aria-expanded="true" aria-controls="collapseOne">
                Accordion Item #1
              </button>
            </h2>
            <div id="collapseOne" class="accordion-collapse collapse show" aria-labelledby="headingOne"
              data-bs-parent="#accordionExample">
              <div class="accordion-body">
                <strong>This is the first item's accordion body.</strong> It is shown by default, until the collapse
                plugin adds the appropriate classes that we use to style each element. These classes control the overall
                appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with
                custom
                CSS or overriding our default variables. It's also worth noting that just about any HTML can go within
                the
                <code>.accordion-body</code>, though the transition does limit overflow.
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <h2 class="accordion-header" id="headingTwo">
              <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse"
                data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
                Accordion Item #2
              </button>
            </h2>
            <div id="collapseTwo" class="accordion-collapse collapse" aria-labelledby="headingTwo"
              data-bs-parent="#accordionExample">
              <div class="accordion-body">
                <strong>This is the second item's accordion body.</strong> It is hidden by default, until the collapse
                plugin adds the appropriate classes that we use to style each element. These classes control the overall
                appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with
                custom
                CSS or overriding our default variables. It's also worth noting that just about any HTML can go within
                the
                <code>.accordion-body</code>, though the transition does limit overflow.
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <h2 class="accordion-header" id="headingThree">
              <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse"
                data-bs-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
                Accordion Item #3
              </button>
            </h2>
            <div id="collapseThree" class="accordion-collapse collapse" aria-labelledby="headingThree"
              data-bs-parent="#accordionExample">
              <div class="accordion-body">
                <strong>This is the third item's accordion body.</strong> It is hidden by default, until the collapse
                plugin adds the appropriate classes that we use to style each element. These classes control the overall
                appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with
                custom
                CSS or overriding our default variables. It's also worth noting that just about any HTML can go within
                the
                <code>.accordion-body</code>, though the transition does limit overflow.
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AboutSection",

  data() {
    return {
      terms_title: '',
      terms_content: ''
    };
  },

  methods: {
    async getData() {
      try {
        return await this.$axios.get(`get-settings/about_us`).then(response => {
          this.terms_title = response.data.data.name;
          this.terms_content = response.data.data.value;
          console.log(response.data)
          console.log()
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
  }
};
</script>

<style lang="scss" scoped>
.about_section_content_wrapper {
  padding-block: 50px;
  overflow-x: hidden;

  .section_image_wrapper {
    display: flex;
    align-items: center;
    justify-content: center;

    img {
      width: 50%;
      height: auto;
    }
  }

  .section_subtitle {
    margin-block: 20px 0;
    color: var(--main_theme_clr);
    font-size: 30px;
  }

  .section_title {
    margin-block: 25px;
    color: var(--main_theme_clr);
    font-weight: 800;
    font-size: 40px;
    width: 70%;
  }

  .section_desc {
    word-break: break-word;
    word-spacing: 2px;
    font-size: 16px;
    color: var(--light_gray_clr);
    line-height: 1.6;
    text-align: start;
    width: 85%;
  }
}

@media (max-width: 850px) {
  .about_section_content_wrapper {
    padding-block: 30px;

    .section_image_wrapper {
      img {
        width: 90%;
      }
    }

    .logo_wrapper {
      display: flex;
      justify-content: center;
    }

    .section_subtitle {
      margin-block: 20px 0;
      font-size: 22px;
      text-align: center;
    }

    .section_title {
      margin-block: 25px;
      font-size: 25px;
      width: 100%;
      text-align: center;
    }

    .section_desc {
      word-break: break-word;
      word-spacing: 2px;
      font-size: 16px;
      text-align: center;
      width: 100%;
    }
  }
}

.about_section_content_wrapper .logo_wrapper img {
  max-width: 160px;
  object-fit: contain;
}
</style>
