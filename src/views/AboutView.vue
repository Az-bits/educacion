<template>
  <div>
    <div class="page-title-area bg-overlay bg-overlay-img banner-img">
      <div class="container">
        <div class="row">
          <div class="col-lg-7">
            <div class="breadcrumb-inner">
              <h2 class="page-title">SOBRE NOSOTROS</h2>
              <ul class="page-list">
                <li><router-link to="/">INICIO</router-link></li>
                <li>ACERCA DE</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="about-area pd-top-50 pd-bottom-90">
      <div class="container">
        <div class="row">
          <div class="col-lg-6">
            <div class="row">
              <div class="col-sm-6 mt-lg-5">
                <!-- <div
                  class="thumb about-thumb wow animated zoomIn"
                  data-wow-duration="0.8s"
                  data-wow-delay="0.1s"
                >
                  <img src="@/assets/sie.png" alt="img" />
                </div> -->
                <div
                  class="thumb about-thumb wow animated zoomIn"
                  data-wow-duration="0.8s"
                  data-wow-delay="0.2s"
                >
                  <img src="@/assets/sie.png" alt="img" />
                </div>
              </div>
              <div class="col-sm-6">
                <div
                  class="thumb about-thumb wow animated zoomIn"
                  data-wow-duration="0.8s"
                  data-wow-delay="0.3s"
                >
                  <img
                    :src="
                      url_api +
                      '/InstitucionUpea/' +
                      Institucion.institucion_logo
                    "
                    alt="img"
                  />
                </div>
                <div
                  class="thumb about-thumb wow animated zoomIn"
                  data-wow-duration="0.8s"
                  data-wow-delay="0.4s"
                >
                  <img src="@/assets/upea.png" alt="img" />
                </div>
              </div>
            </div>
          </div>
          <div class="col-lg-6 align-self-center mt-4 mt-lg-0">
            <div class="section-title style-bg mb-0">
              <h5 class="sub-title">Sobre la carrera</h5>
              <h2 class="title">{{ Institucion.institucion_nombre }}</h2>
              <div class="single-list-inner mt-4">
                <ul>
                  <li>
                    <i class="fa fa-check"></i> Mision
                    <p v-html="Institucion.institucion_mision"></p>
                  </li>
                  <li>
                    <i class="fa fa-check"></i> Vision
                    <p v-html="Institucion.institucion_vision"></p>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="counter-area pd-bottom-90">
      <div class="container">
        <div class="row">
          <div class="col-lg-3 col-md-6">
            <div class="single-counter-inner after-bg">
              <div class="media">
                <div class="media-left">
                  <div class="thumb">
                    <img src="@/assets/img/icon/1.png" alt="img" />
                  </div>
                </div>
                <div class="media-body">
                  <div class="details">
                    <h2>
                      <span class="counter">{{ Conv.length }}</span>
                    </h2>
                    <p>Convocatorias, comunicados & avisos</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-lg-3 col-md-6">
            <div class="single-counter-inner after-bg">
              <div class="media">
                <div class="media-left">
                  <div class="thumb">
                    <img src="@/assets/img/icon/2.png" alt="img" />
                  </div>
                </div>
                <div class="media-body">
                  <div class="details">
                    <h2>
                      <span class="counter">{{ Cur.length }}</span>
                    </h2>
                    <p>Cursos & seminarios</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-lg-3 col-md-6">
            <div class="single-counter-inner after-bg">
              <div class="media">
                <div class="media-left">
                  <div class="thumb">
                    <img src="@/assets/img/icon/3.png" alt="img" />
                  </div>
                </div>
                <div class="media-body">
                  <div class="details">
                    <h2>
                      <span class="counter">{{ Serv.length }}</span>
                    </h2>
                    <p>Servicios</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-lg-3 col-md-6">
            <div class="single-counter-inner after-bg">
              <div class="media">
                <div class="media-left">
                  <div class="thumb">
                    <img src="@/assets/img/icon/5.png" alt="img" />
                  </div>
                </div>
                <div class="media-body">
                  <div class="details">
                    <h2>
                      <span>{{ Ofer.length }}</span>
                    </h2>
                    <p>Ofertas académicas</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div
      class="
        about-area about-right-bg-half
        bg-gray
        pd-top-120 pd-bottom-90
        banner-img
      "
    >
      <div class="container">
        <div class="row">
          <div class="col-lg-6 bg-gray">
            <div class="section-title">
              <h2 class="title">Sobre la carrera</h2>
              <p class="content" v-html="Institucion.institucion_sobre_ins"></p>
            </div>
          </div>
          <div class="col-lg-6">
            <img src="@/assets/upea_fondo.jpg" alt="fondo" />
          </div>
        </div>
      </div>
    </div>

    <div class="team-area pd-top-115 pd-bottom-60">
      <div class="container">
        <div class="row">
          <div class="col-12">
            <div class="section-title text-center">
              <h6 class="sub-title">Autoridades</h6>
              <h2 class="title">Nuestras autoridades</h2>
            </div>
          </div>
        </div>
        <div class="row justify-content-center">
          <div
            class="col-lg-4 col-md-6"
            v-for="(autoridad, id_aut) of Institucion.autoridad"
            :key="id_aut"
            v-show="
              (pag - 1) * NUM_RESULTS <= id_aut && pag * NUM_RESULTS > id_aut
            "
          >
            <div class="single-team-inner">
              <div class="thumb thumb-img">
                <img
                  :src="
                    url_api +
                    '/InstitucionUpea/Autoridad/' +
                    autoridad.foto_autoridad
                  "
                  alt="img"
                />
              </div>
              <div class="details pt-5">
                <ul class="team-social-media">
                  <li>
                    <a
                      :href="'https://wa.me/+' + autoridad.celular_autoridad"
                      target="_blank"
                      ><i class="fa fa-whatsapp" aria-hidden="true"></i
                    ></a>
                  </li>
                  <li>
                    <a :href="autoridad.facebook_autoridad" target="_blank"
                      ><i class="fa fa-facebook" aria-hidden="true"></i
                    ></a>
                  </li>
                  <li>
                    <a :href="autoridad.twiter_autoridad" target="_blank"
                      ><i class="fa fa-twitter" aria-hidden="true"></i
                    ></a>
                  </li>
                </ul>
                <h5>
                  <a href="single-team.html">{{
                    autoridad.nombre_autoridad
                  }}</a>
                  <span> - {{ autoridad.cargo_autoridad }}</span>
                </h5>
              </div>
            </div>
          </div>
          <nav
            class="col-12 td-page-navigation text-center mb-5 mb-lg-0"
            v-show="pager > 1"
          >
            <ul class="pagination">
              <li class="pagination-arrow disable">
                <a
                  href="#"
                  aria-label="Previous"
                  @click.prevent="pag != 1 ? (pag -= 1) : ''"
                >
                  <i class="fa fa-angle-double-left"></i>
                </a>
              </li>
              <li v-for="(i, index) of pager" :key="index">
                <a
                  href="#"
                  :class="[i == pag ? 'active' : '']"
                  @click.prevent="pag = i"
                >
                  {{ i }}
                </a>
              </li>
              <li class="pagination-arrow">
                <a
                  href="#"
                  aria-label="Next"
                  @click.prevent="pag != pager ? (pag += 1) : ''"
                  ><i class="fa fa-angle-double-right"></i
                ></a>
                <!-- v-show="(pag * NUM_RESULTS) / Cursos.length < 1" -->
              </li>
            </ul>
          </nav>
        </div>
      </div>
    </div>

    <div class="container">
      <div class="row">
        <div class="col-lg-3" style="display: flex; align-items: center">
          <div class="section-title">
            <h2 class="title">
              Historia de la institucion
              <img
                :src="
                  url_api + '/InstitucionUpea/' + Institucion.institucion_logo
                "
                alt=""
              />
            </h2>
          </div>
        </div>
        <div class="col-lg-9 bg-gray">
          <div class="section-title">
            <p class="content" v-html="Institucion.institucion_historia"></p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "AboutView",
  data() {
    return {
      Conv: [],
      Cur: [],
      Serv: [],
      Ofer: [],

      NUM_RESULTS: 3,
      pag: 1,
      pager: 0,
    };
  },
  computed: {
    ...mapState(["Institucion", "url_api"]),
  },
  methods: {
    async getConvocatoriasAll() {
      try {
        let res = await this.axios.get(
          "/api/convocatoriasAll/" + process.env.VUE_APP_ID_CARRERA
        );
        this.Conv = res.data;
        this.pager = this.Institucion.autoridad.length / this.NUM_RESULTS;
        if (this.pager - Math.trunc(this.pager) > 0) {
          this.pager = Math.trunc(this.pager) + 1;
        }
      } catch (error) {
        console.log(error);
      }
    },
    async getCursosAll() {
      try {
        let res = await this.axios.get(
          "/api/cursosAll/" + process.env.VUE_APP_ID_CARRERA
        );
        this.Cur = res.data;
      } catch (error) {
        console.log(error);
      }
    },
    async getServiciosAll() {
      try {
        let res = await this.axios.get(
          "/api/ServicioAll/" + process.env.VUE_APP_ID_CARRERA
        );
        this.Serv = res.data;
      } catch (error) {
        console.log(error);
      }
    },
    async getOfertasAll() {
      try {
        let res = await this.axios.get(
          "/api/OfertasAcademicasAll/" + process.env.VUE_APP_ID_CARRERA
        );
        this.Ofer = res.data;
        this.$store.commit("loading");
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.$store.commit("loadOn");
    this.getConvocatoriasAll();
    this.getCursosAll();
    this.getServiciosAll();
    this.getOfertasAll();
  },
};
</script>