<template>
  <!-- :class="{ sticky: scrollPosition > 50 }" -->
  <div id="navbar" class="header_content_wrapper">
    <div class="container-xl py-0">
      <!-- Start:: Logo -->
      <div class="logo_wrapper">
        <nuxt-link :to="localePath('/')">
          <img src="~/assets/media/logo/logo.png" width="100" height="auto" alt="Logo" />
        </nuxt-link>
      </div>
      <!-- End:: Logo -->

      <!-- Start:: Navbar Routes -->
      <div class="routes_wrapper">
        <ul class="routes_list">
          <!-- <li class="navbar_route">
            <button :class="$route.path == localePath('/') ? 'active' : ''" @click="scrollToSection('hero_section')">
              {{ $t('nav.home') }}
            </button>
          </li> -->

          <li class="navbar_route">
            <b-dropdown id="dropdown-1" :text="$t('nav.home')" class="m-md-2">
              <b-dropdown-item v-for="(item, index) in questions" :key="'k' + index"
                @click="handleDropdownClick(item.answer)">
                {{ item.question }}
              </b-dropdown-item>
            </b-dropdown>
          </li>

          <li class="navbar_route">
            <nuxt-link :to="localePath('/tilawati-app')">
              {{ $t('pages.project_name') }}
            </nuxt-link>
          </li>

          <li class="navbar_route">
            <nuxt-link :to="localePath('/project-details')">
              {{ $t('pages.project_details') }}
            </nuxt-link>
          </li>

          <li class="navbar_route">
            <button @click="scrollToSection('about_section')">
              {{ $t('nav.about') }}
            </button>
          </li>

          <li class="navbar_route">
            <button @click="scrollToSection('app_screens_section')">
              {{ $t('nav.screen') }}
            </button>
          </li>

          <li class="navbar_route">
            <button @click="scrollToSection('download_app_section')">
              {{ $t('nav.download') }}
            </button>
          </li>

          <li class="navbar_route">
            <nuxt-link :to="localePath('/terms')">
              {{ $t('nav.terms') }}
            </nuxt-link>
          </li>

          <li class="navbar_route">
            <nuxt-link :to="localePath('/policy')">
              {{ $t('nav.policy') }}
            </nuxt-link>
          </li>

          <li class="navbar_route">
            <nuxt-link :to="localePath('/contact')">
              {{ $t('nav.contact') }}
            </nuxt-link>
          </li>

          <li class="navbar_route">
            <template v-if="$i18n.locale == 'en'">
              <nuxt-link v-for="(locale, i) in showLocales" :key="i" :to="switchLocalePath(locale.code)">
                <span class="icon" @click="changelang">
                  <!-- <img src="~/assets/media/icons/ar.png" width="30" alt="Arabic Flag"> -->
                  ع
                </span>
              </nuxt-link>
            </template>

            <template v-if="$i18n.locale == 'ar'">
              <nuxt-link v-for="(locale, i) in showLocales" :key="i" :to="switchLocalePath(locale.code)">
                <span class="icon" @click="changelang">
                  <!-- <img src="~/assets/media/icons/en.png" width="30" alt="English Flag"> -->
                  en
                </span>
              </nuxt-link>
            </template>
          </li>
        </ul>
      </div>
      <!-- End:: Navbar Routes -->

      <!-- Start:: Navbar Buttons -->
      <div class="navbar_btns_wrapper">
        <button class="small_screens_menu" @click="toggleSmallScreensNavbarDrawer">
          <i class="fa-solid fa-ellipsis"></i>
        </button>
      </div>
      <!-- End:: Navbar Buttons -->
    </div>

    <!-- Start:: Small Screens Nav Drawer -->
    <div class="small_screens_nav_bar_wrapper" :class="{ active: smallScreensMenuIsOpen }">
      <div class="small_screen_menu_close_btn">
        <button @click="toggleSmallScreensNavbarDrawer">
          <i class="fas fa-times fa-lg"></i>
        </button>
      </div>

      <ul class="small_screens_nav_bar_links_list">
        <!-- <li class="links_list_item" @click="toggleSmallScreensNavbarDrawer">
          <button :class="$route.path == localePath('/') ? 'active' : ''" @click="scrollToSection('hero_section')">
            {{ $t('nav.home') }}
          </button>
        </li> -->

         <li class="links_list_item mx-15" >
            <b-dropdown id="dropdown-1" :text="$t('nav.home')" class="">
              <b-dropdown-item v-for="(item, index) in questions" :key="'k' + index"
                @click="handleDropdownClick(item.answer)">
                {{ item.question }}
              </b-dropdown-item>
            </b-dropdown>
          </li>

        <li class="links_list_item" @click="toggleSmallScreensNavbarDrawer">
          <button @click="scrollToSection('about_section')">
            {{ $t('nav.about') }}
          </button>
        </li>

        <li class="links_list_item" @click="toggleSmallScreensNavbarDrawer">
          <button @click="scrollToSection('app_screens_section')">
            {{ $t('nav.screen') }}
          </button>
        </li>

        <li class="links_list_item" @click="toggleSmallScreensNavbarDrawer">
          <button @click="scrollToSection('download_app_section')">
            {{ $t('nav.download') }}
          </button>
        </li>

        <li class="links_list_item" @click="toggleSmallScreensNavbarDrawer">
          <button @click="scrollToSection('contact_us_section')">
            {{ $t('nav.contact') }}
          </button>
        </li>

        <li class="links_list_item" @click="toggleSmallScreensNavbarDrawer">
          <nuxt-link :to="localePath('/terms')">
            {{ $t('nav.terms') }}
          </nuxt-link>
        </li>

        <li class="links_list_item">
          <nuxt-link v-for="(locale, i) in showLocales" :key="i" :to="switchLocalePath(locale.code)">
            <span class="icon"><i class="fas fa-globe"></i></span>
          </nuxt-link>
        </li>
      </ul>
    </div>
    <!-- End:: Small Screens Nav Drawer -->
  </div>
</template>

<script>
export default {
  name: 'TheNavbar',

  data() {
    return {
      smallScreensMenuIsOpen: false,
      scrollPosition: null,

      questions: []
    }
  },

  methods: {

    handleDropdownClick(newHeaderText) {
      this.$store.commit('updateHeaderText', newHeaderText)
    },

    changelang() {
      setTimeout(() => {
        location.reload()
      }, 1000)
    },
    // START:: SCROLL TO SECTION
    scrollToSection(section_id) {
      if (this.$route.path != this.localePath('/')) {
        this.$router.push(this.localePath('/'))
      } else {
        const selected_section = document.querySelector(`#${section_id}`)
        selected_section.scrollIntoView({ behavior: 'auto' })
      }
    },
    // END:: SCROLL TO SECTION

    toggleSmallScreensNavbarDrawer() {
      this.smallScreensMenuIsOpen = !this.smallScreensMenuIsOpen
    },

    // START:: HANDLING STICKY HEADER
    updateScroll() {
      this.scrollPosition = window.scrollY
    },
    // END:: HANDLING STICKY HEADER
    async getData() {
      try {
        return await this.$axios.get(`questions`).then(response => {
          this.isLoading = true;
          this.questions = response.data.data;
          this.$store.commit('updateHeaderText', response.data.data[0].answer)
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
    // START:: FIRE METHODS
    window.addEventListener('scroll', this.updateScroll, { passive: true })
    // END:: FIRE METHODS
  },


  computed: {
    locales() {
      return this.$i18n.locales.filter((i) => i.code)
    },
    showLocales() {
      return this.$i18n.locales.filter((i) => i.code !== this.$i18n.locale)
    },
  },

}
</script>

<style lang="scss" scoped>

</style>
