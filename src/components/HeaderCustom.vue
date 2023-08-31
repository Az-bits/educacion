<template>
  <header class="main-header clearfix">
    <HeaderContent></HeaderContent>
  </header>
  <div class="stricky-header stricked-menu main-menu">
    <div class="sticky-header__content">
      <HeaderContent></HeaderContent>
    </div>
  </div>
</template>

<style scoped>
.logo_carrera {
  display: flex;
  align-items: center;
}

.logo_carrera h3 {
  color: white;
  padding: 5px;
}
</style>

<script>
import HeaderContent from "@/components/HeaderContent.vue";
import { mapState } from "vuex";
export default {
  components: {
    HeaderContent
  },
  data() {
    return {
      sopen: false,
      Links: [],

      m_inicio: false,
      m_conv: false,
      m_cur: false,
      m_mas: false,
      m_link: false,
    };
  },
  computed: {
    ...mapState(["url_api", "MenuConv", "MenuCur", "Institucion", "getter"]),
  },
  methods: {
    click_m() {
      this.$store.commit("clickLink");
      this.$store.commit("idEncrypt")
      this.openMenu();
    },
    showSubMenu(id) {
      switch (id) {
        case "m_inicio":
          this.m_inicio = true;
          this.m_conv = false;
          this.m_cur = false;
          this.m_mas = false;
          this.m_link = false;
          break;
        case "m_conv":
          this.m_inicio = false;
          this.m_conv = true;
          this.m_cur = false;
          this.m_mas = false;
          this.m_link = false;
          break;
        case "m_cur":
          this.m_inicio = false;
          this.m_conv = false;
          this.m_cur = true;
          this.m_mas = false;
          this.m_link = false;
          break;
        case "m_mas":
          this.m_inicio = false;
          this.m_conv = false;
          this.m_cur = false;
          this.m_mas = true;
          this.m_link = false;
          break;
        case "m_link":
          this.m_inicio = false;
          this.m_conv = false;
          this.m_cur = false;
          this.m_mas = false;
          this.m_link = true;
          break;

        default:
          console.log("");
          break;
      }
    },
    openMenu() {
      this.sopen = !this.sopen;
    },
    async getLinks() {
      try {
        let res = await this.axios.get(
          "/api/linksIntExtAll/" + process.env.VUE_APP_ID_INSTITUCION
        );
        this.Links = res.data;
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.getLinks();
  },
  mounted() {
    if (this.getter) {
      this.getLinks();
      this.$store.state.getter = false;
    }
  },
};
</script>