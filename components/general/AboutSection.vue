<template>
  <div id="about_section" class="about_section_content_wrapper">
    <div class="section_image_wrapper">
      <img src="~/assets/media/images/about.png" width="450" height="350" alt="About Us Section Image" loading="lazy" />
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
      width: 100%;
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
        width: 100%;
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
