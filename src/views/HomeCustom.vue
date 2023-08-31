<template>
  <div>
    <div class="banner-area banner-area-1 banner-bg-overlay banner-img">
      <div class="container">
        <div class="row bg-tr">
          <div class="col-10">
            <div class="banner-inner style-white text-center text-lg-left">
              <h1 class="al-animate-2 title pd-top-100">
                {{ Institucion.institucion_nombre }}
              </h1>
              <p
                class="al-animate-3 pd-top-50"
                v-html="Institucion.institucion_objetivos"
                style="font-size: 15px"
              ></p>
              <br /><br />
              <a class="btn btn-base al-animate-4" href="#intro-area">
                Ver novedades
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- counter area start -->
    <div class="counter-area">
      <div class="container">
        <div class="row">
          <div class="col-lg-4">
            <div class="single-quote-inner">
              <div class="thumb text-right">
                <img src="@/assets/upea.png" alt="img" width="77%" />
              </div>
              <br />
              <div class="details">
                <h4>Formación de profesionales</h4>
              </div>
            </div>
          </div>
          <div class="col-lg-8 pd-top-90">
            <div class="block-area">
              <h3>LINKS EXTERNOS</h3>
              <div class="row">
                <a
                  class="col-md-6"
                  v-for="(link, id_link) of Links"
                  :key="id_link"
                  :href="link.ei_link"
                  target="_blank"
                >
                  <div
                    class="single-block-inner single-block-inner-1"
                    :style="
                      'background-image: url(' +
                      url_api +
                      '/InstitucionUpea/LinksExternos/' +
                      link.ei_imagen +
                      ');object-fit:cover'
                    "
                  >
                    <div class="cat">{{ link.ei_tipo }}</div>
                    <h4>{{ link.ei_nombre }}</h4>
                  </div>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- counter end -->
    <div id="intro-area" style="height: 50px"></div>
    <!-- intro area start -->
    <div class="intro-area pd-top-90">
      <div class="container">
        <div class="section-title text-center">
          <h5 class="sub-title">Categorías</h5>
          <h2 class="title">Explorar contenido</h2>
        </div>
        <div class="row">
          <router-link
            class="col-lg-3 col-md-3 col-sm-6 card-intro"
            v-for="(conv, id_conv) of MenuConv"
            :key="id_conv"
            :to="'/convocatorias/' + conv.idtipo_conv_comun"
            @click="$store.commit('clickLink')"
          >
            <div class="single-intro-inner bg-base style-two text-center">
              <div class="thumb cat-thumb">
                <img src="@/assets/img/intro/5.png" alt="img" />
              </div>
              <div class="details">
                <h5>
                  <span>{{ contarConv(conv.tipo_conv_comun_titulo) }}</span>
                  &nbsp;
                  {{ conv.tipo_conv_comun_titulo }}
                </h5>
              </div>
            </div>
          </router-link>
          <router-link
            class="col-lg-3 col-md-3 col-sm-6 card-intro"
            v-for="(cur, id_cur) of MenuCur"
            :key="id_cur"
            :to="'/cursos/' + cur.idtipo_curso_otros"
            @click="$store.commit('clickLink')"
          >
            <div class="single-intro-inner bg-base-2 style-two text-center">
              <div class="thumb cat-thumb">
                <img src="@/assets/img/intro/5.png" alt="img" />
              </div>
              <div class="details">
                <h5>
                  <span>{{ contarCur(cur.tipo_conv_curso_nombre) }}</span>
                  &nbsp;
                  {{ cur.tipo_conv_curso_nombre }}
                </h5>
              </div>
            </div>
          </router-link>
          <router-link
            to="/servicios"
            class="col-lg-3 col-md-3 col-sm-6 card-intro"
          >
            <div class="single-intro-inner bg-red style-two text-center">
              <div class="thumb cat-thumb">
                <img src="@/assets/img/intro/3.png" alt="img" />
              </div>
              <div class="details">
                <h5>
                  <span>{{ Serv.length }}</span>
                  &nbsp; SERVICIOS
                </h5>
              </div>
            </div>
          </router-link>
          <router-link
            to="/ofertas"
            class="col-lg-3 col-md-3 col-sm-6 card-intro"
          >
            <div class="single-intro-inner bg-purple style-two text-center">
              <div class="thumb cat-thumb">
                <img src="@/assets/img/intro/4.png" alt="img" />
              </div>
              <div class="details">
                <h5>
                  <span>{{ Ofer.length }}</span>
                  &nbsp; OFERTAS ACADÉMICAS
                </h5>
              </div>
            </div>
          </router-link>
          <router-link
            to="/publicaciones"
            class="col-lg-3 col-md-3 col-sm-6 card-intro"
          >
            <div class="single-intro-inner bg-pink style-two text-center">
              <div class="thumb cat-thumb">
                <img src="@/assets/img/intro/5.png" alt="img" />
              </div>
              <div class="details">
                <h5>
                  <span>{{ Publi.length }}</span>
                  &nbsp; PUBLICACIONES
                </h5>
              </div>
            </div>
          </router-link>
          <router-link
            to="/gaceta"
            class="col-lg-3 col-md-3 col-sm-6 card-intro"
          >
            <div class="single-intro-inner bg-base style-two text-center">
              <div class="thumb cat-thumb">
                <img src="@/assets/img/intro/6.png" alt="img" />
              </div>
              <div class="details">
                <h5>
                  <span>{{ Gac.length }}</span>
                  &nbsp; GACETA
                </h5>
              </div>
            </div>
          </router-link>
          <router-link
            to="/eventos"
            class="col-lg-3 col-md-3 col-sm-6 card-intro"
          >
            <div class="single-intro-inner bg-base-2 style-two text-center">
              <div class="thumb cat-thumb">
                <img src="@/assets/img/intro/1.png" alt="img" />
              </div>
              <div class="details">
                <h5>
                  <span>{{ Event.length }}</span>
                  &nbsp; EVENTOS
                </h5>
              </div>
            </div>
          </router-link>
          <router-link
            to="/videos"
            class="col-lg-3 col-md-3 col-sm-6 card-intro"
          >
            <div class="single-intro-inner bg-base-3 style-two text-center">
              <div class="thumb cat-thumb">
                <img src="@/assets/img/intro/1.png" alt="img" />
              </div>
              <div class="details">
                <h5>
                  <span>{{ Vid.length }}</span>
                  &nbsp; VIDEOS
                </h5>
              </div>
            </div>
          </router-link>
        </div>
      </div>
    </div>
    <!-- intro area end -->

    <!-- about area start -->
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
              <p class="content" v-html="Institucion.institucion_sobre_ins"></p>
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
    <!-- about area end -->

    <!-- call to action area start -->
    <div
      class="call-to-action-area bg-cover pd-top-110 pd-bottom-120 fondo-img"
    >
      <div class="container">
        <div class="row">
          <div class="col-12 col-lg-4">
            <div
              class="section-title mb-0 style-white d-flex align-items-center"
            >
              <h2 class="title">
                Video vision {{ Institucion.institucion_nombre }}
              </h2>
              <!-- <a class="btn btn-black" href="course.html">Find Out More</a> -->
            </div>
          </div>
          <div class="col-12 col-lg-8">
            <iframe
              :src="Institucion.institucion_link_video_vision"
              frameborder="0"
              style="width: 100%; min-height: 400px"
              allowfullscreen="allowfullscreen"
            ></iframe>
          </div>
        </div>
      </div>
    </div>
    <!-- call to action area start -->

    <!--team-area start-->
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
                <!-- <p><i class="fa fa-user"></i> 100+ Courses</p> -->
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
    <!--team-area end-->

    <!--event-area start-->
    <div class="event-area mg-bottom-120">
      <div class="container">
        <div class="row no-gutters">
          <div class="col-xl-7 col-lg-6 bg-overlay bg-cover bg-cover-img">
            <div class="event-section-title">
              <div class="section-title mb-0 pt-xl-5 style-white">
                <h5 class="sub-title">Organigrama</h5>
                <h2 class="title">
                  Organización y estructura administrativa de la carrera
                </h2>
                <!-- <a class="btn btn-border-white" href="event.html">All Events</a> -->
              </div>
            </div>
          </div>
          <div class="col-xl-5 col-lg-6">
            <div class="event-area-inner bg-base-3">
              <a
                :href="
                  url_api +
                  '/InstitucionUpea/' +
                  Institucion.institucion_organigrama
                "
                target="_blank"
              >
                <vue-pdf-embed
                  :source="
                    url_api +
                    '/InstitucionUpea/' +
                    Institucion.institucion_organigrama
                  "
                  :page="1"
                  height="410"
                />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!--event-area end-->

    <!--blog-area start-->
    <div class="blog-area pd-top-115 mb-5 pb-3">
      <div class="container">
        <div class="row justify-content-center">
          <div class="col-xl-6 col-lg-7 col-md-11">
            <div class="section-title text-center">
              <h5 class="sub-title">Lo mas reciente</h5>
              <h2 class="title">
                Convocatorias, comunicados, avisos recientes
              </h2>
            </div>
          </div>
        </div>
        <div
          v-if="
            Object.keys(latestConv).length +
              Object.keys(latestComun).length +
              Object.keys(latestAv).length >
            0
          "
          class="row justify-content-center"
        >
          <div
            class="col-lg-4 col-md-6"
            v-if="Object.keys(latestConv).length != 0"
          >
            <div class="single-blog-inner">
              <div class="thumb">
                <router-link
                  :to="'/detalleConvocatoria/' + latestConv.idconvocatorias"
                >
                  <img
                    :src="
                      url_api + '/Convocatorias/' + latestConv.con_foto_portada
                    "
                    alt="img"
                  />
                </router-link>
              </div>
              <div class="details">
                <div class="blog-meta">
                  <ul>
                    <router-link
                      :to="
                        '/convocatorias/' +
                        latestConv.tipo_conv_comun.idtipo_conv_comun
                      "
                    >
                      <li class="comnt bg-base">
                        {{ latestConv.tipo_conv_comun.tipo_conv_comun_titulo }}
                      </li>
                    </router-link>
                    &nbsp;
                    <li class="date">{{ dmy(latestConv.con_fecha_inicio) }}</li>
                  </ul>
                </div>
                <h4>
                  <router-link
                    :to="'/detalleConvocatoria/' + latestConv.idconvocatorias"
                    >{{ latestConv.con_titulo }}</router-link
                  >
                </h4>
                <router-link
                  :to="'/detalleConvocatoria/' + latestConv.idconvocatorias"
                  class="readmore-text"
                  >Leer mas</router-link
                >
              </div>
            </div>
          </div>
          <div
            class="col-lg-4 col-md-6"
            v-if="Object.keys(latestComun).length != 0"
          >
            <div class="single-blog-inner">
              <div class="thumb">
                <router-link
                  :to="'/detalleConvocatoria/' + latestComun.idconvocatorias"
                >
                  <img
                    :src="
                      url_api + '/Convocatorias/' + latestComun.con_foto_portada
                    "
                    alt="img"
                  />
                </router-link>
              </div>
              <div class="details">
                <div class="blog-meta">
                  <ul>
                    <router-link
                      :to="
                        '/convocatorias/' +
                        latestComun.tipo_conv_comun.idtipo_conv_comun
                      "
                    >
                      <li class="comnt bg-base">
                        {{ latestComun.tipo_conv_comun.tipo_conv_comun_titulo }}
                      </li>
                    </router-link>
                    &nbsp;
                    <li class="date">
                      {{ dmy(latestComun.con_fecha_inicio) }}
                    </li>
                  </ul>
                </div>
                <h4>
                  <router-link
                    :to="'/detalleConvocatoria/' + latestComun.idconvocatorias"
                  >
                    {{ latestComun.con_titulo }}
                  </router-link>
                </h4>
                <router-link
                  :to="'/detalleConvocatoria/' + latestComun.idconvocatorias"
                  class="readmore-text"
                  >Leer mas</router-link
                >
              </div>
            </div>
          </div>
          <div
            class="col-lg-4 col-md-6"
            v-if="Object.keys(latestAv).length != 0"
          >
            <div class="single-blog-inner">
              <div class="thumb">
                <router-link
                  :to="'/detalleConvocatoria/' + latestAv.idconvocatorias"
                >
                  <img
                    :src="
                      url_api + '/Convocatorias/' + latestAv.con_foto_portada
                    "
                    alt="img"
                  />
                </router-link>
              </div>
              <div class="details">
                <div class="blog-meta">
                  <ul>
                    <router-link
                      :to="
                        '/convocatorias/' +
                        latestAv.tipo_conv_comun.idtipo_conv_comun
                      "
                    >
                      <li class="comnt bg-base">
                        {{ latestAv.tipo_conv_comun.tipo_conv_comun_titulo }}
                      </li>
                    </router-link>
                    &nbsp;
                    <li class="date">{{ dmy(latestAv.con_fecha_inicio) }}</li>
                  </ul>
                </div>
                <h4>
                  <router-link
                    :to="'/detalleConvocatoria/' + latestAv.idconvocatorias"
                    >{{ latestAv.con_titulo }}</router-link
                  >
                </h4>
                <router-link
                  :to="'/detalleConvocatoria/' + latestAv.idconvocatorias"
                  class="readmore-text"
                  >Leer mas</router-link
                >
              </div>
            </div>
          </div>
        </div>
        <div
          v-if="
            Object.keys(latestCur).length + Object.keys(latestSem).length > 0
          "
        >
          <div class="row justify-content-center">
            <div class="col-xl-6 col-lg-7 col-md-11">
              <div class="section-title text-center">
                <h2 class="title">Cursos, seminarios recientes</h2>
              </div>
            </div>
          </div>
          <div class="row justify-content-center">
            <div
              class="col-lg-4 col-md-6"
              v-if="Object.keys(latestCur).length != 0"
            >
              <div class="single-blog-inner">
                <div class="thumb">
                  <router-link
                    :to="
                      '/detalleCurso/' + latestCur.iddetalle_cursos_academicos
                    "
                  >
                    <img
                      :src="url_api + '/Cursos/' + latestCur.det_img_portada"
                      alt="img"
                    />
                  </router-link>
                </div>
                <div class="details">
                  <div class="blog-meta">
                    <ul>
                      <router-link
                        :to="'/cursos/' + latestCur.idtipo_curso_otros"
                      >
                        <li class="comnt bg-base">
                          {{ latestCur.tipo_curso_otro.tipo_conv_curso_nombre }}
                        </li>
                      </router-link>
                      &nbsp;
                      <li class="date">{{ dmy(latestCur.det_fecha_ini) }}</li>
                    </ul>
                  </div>
                  <h4>
                    <router-link
                      :to="
                        '/detalleCurso/' + latestCur.iddetalle_cursos_academicos
                      "
                    >
                      {{ latestCur.det_titulo }}
                    </router-link>
                  </h4>
                  <router-link
                    :to="
                      '/detalleCurso/' + latestCur.iddetalle_cursos_academicos
                    "
                    class="readmore-text"
                  >
                    Leer mas
                  </router-link>
                </div>
              </div>
            </div>
            <div
              class="col-lg-4 col-md-6"
              v-if="Object.keys(latestSem).length != 0"
            >
              <div class="single-blog-inner">
                <div class="thumb">
                  <router-link
                    :to="
                      '/detalleCurso/' + latestSem.iddetalle_cursos_academicos
                    "
                  >
                    <img
                      :src="url_api + '/Cursos/' + latestSem.det_img_portada"
                      alt="img"
                    />
                  </router-link>
                </div>
                <div class="details">
                  <div class="blog-meta">
                    <ul>
                      <router-link
                        :to="'/detalleCurso/' + latestSem.idtipo_curso_otros"
                      >
                        <li class="comnt bg-base">
                          {{ latestSem.tipo_curso_otro.tipo_conv_curso_nombre }}
                        </li>
                      </router-link>
                      &nbsp;
                      <li class="date">{{ dmy(latestSem.det_fecha_ini) }}</li>
                    </ul>
                  </div>
                  <h4>
                    <router-link
                      :to="
                        '/detalleCurso/' + latestSem.iddetalle_cursos_academicos
                      "
                    >
                      {{ latestSem.det_titulo }}
                    </router-link>
                  </h4>
                  <router-link
                    :to="
                      '/detalleCurso/' + latestSem.iddetalle_cursos_academicos
                    "
                    class="readmore-text"
                    >Leer mas</router-link
                  >
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="container">
          <h3>
            <i class="fa fa-map-marker"></i>
            {{ Institucion.institucion_direccion }}
          </h3>
          <iframe
            :src="Institucion.institucion_api_google_map"
            width="85%"
            height="400"
            frameborder="0"
          ></iframe>
        </div>
      </div>
    </div>
    <!--blog-area end-->
  </div>
</template>

<style scoped>
.banner-img {
  background-image: url("@/assets/Fondo2.jpg");
}
.fondo-img {
  background-image: url("@/assets/upea_fondo.jpg");
  background-repeat: no-repeat;
  background-attachment: fixed;
  object-fit: cover;
  background-size: 100%;
}
.bg-cover-img {
  background-image: url("@/assets/fondo_upea.jpg");
}
.thumb-img {
  filter: drop-shadow(-2px 2px 15px #000000b3);
}
.card-intro:hover h5 {
  color: var(--main-color-1);
  user-select: none;
}
.bg-tr {
  backdrop-filter: blur(5px);
  background-color: rgba(0, 0, 0, 0.25);
  padding-left: 70px;
  padding-bottom: 50px;
  border-radius: 50px;
}
</style>

<script>
import { mapState } from "vuex";
import VuePdfEmbed from "vue-pdf-embed";
export default {
  name: "HomeCustom",
  data() {
    return {
      Conv: 0,
      latestConv: {},
      latestComun: {},
      latestAv: {},

      Cur: 0,
      latestCur: {},
      latestSem: {},

      Serv: [],
      Ofer: [],
      Publi: [],
      Gac: [],
      Event: [],
      Vid: [],

      NUM_RESULTS: 3,
      pag: 1,
      pager: 0,
    };
  },
  computed: {
    ...mapState(["url_api", "Institucion", "MenuConv", "MenuCur", "Links"]),
  },
  components: {
    VuePdfEmbed,
  },
  methods: {
    async getConvocatoriasAll() {
      try {
        let res = await this.axios.get(
          "/api/convocatoriasAll/" + process.env.VUE_APP_ID_CARRERA
        );
        this.Conv = res.data;
        this.Conv.forEach((conv) => {
          if (
            conv.tipo_conv_comun.tipo_conv_comun_titulo == "CONVOCATORIAS" &&
            conv.con_estado == "1"
          ) {
            if (Object.keys(this.latestConv).length == 0) {
              this.latestConv = conv;
            }
          } else {
            if (
              conv.tipo_conv_comun.tipo_conv_comun_titulo == "COMUNICADOS" &&
              conv.con_estado == "1"
            ) {
              if (Object.keys(this.latestComun).length == 0) {
                this.latestComun = conv;
              }
            } else {
              if (
                conv.tipo_conv_comun.tipo_conv_comun_titulo == "AVISOS" &&
                conv.con_estado == "1"
              ) {
                if (Object.keys(this.latestAv).length == 0) {
                  this.latestAv = conv;
                }
              }
            }
          }
        });
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
        this.Cur.forEach((cur) => {
          if (
            cur.tipo_curso_otro.tipo_conv_curso_nombre == "CURSOS" &&
            cur.det_estado == "1"
          ) {
            if (Object.keys(this.latestCur).length == 0) {
              this.latestCur = cur;
            }
          } else {
            if (
              cur.tipo_curso_otro.tipo_conv_curso_nombre == "SEMINARIOS" &&
              cur.det_estado == "1"
            ) {
              if (Object.keys(this.latestSem).length == 0) {
                this.latestSem = cur;
              }
            }
          }
        });
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
      } catch (error) {
        console.log(error);
      }
    },
    async getPublicaciones() {
      try {
        let res = await this.axios.get(
          "/api/publicacionesAll/" + process.env.VUE_APP_ID_INSTITUCION
        );
        this.Publi = res.data;
      } catch (error) {
        console.log(error);
      }
    },
    async getGacetaAll() {
      try {
        let res = await this.axios.get(
          "/api/gacetaunivAll/" + process.env.VUE_APP_ID_INSTITUCION
        );
        this.Gac = res.data;
      } catch (error) {
        console.log(error);
      }
    },
    async getEventos() {
      try {
        let res = await this.axios.get(
          "/api/eventoAll/" + process.env.VUE_APP_ID_INSTITUCION
        );
        this.Event = res.data;
      } catch (error) {
        console.log(error);
      }
    },
    async getVideos() {
      try {
        let res = await this.axios.get(
          "/api/VideosAll/" + process.env.VUE_APP_ID_INSTITUCION
        );
        this.Vid = res.data;
        this.$store.commit("loading");
      } catch (error) {
        console.log(error);
      }
    },
    async setImage(id, img) {
      try {
        await document
          .querySelector("." + id)
          .setAttribute("style", 'background-image: url("' + img + '");');
      } catch (error) {
        console.log(error);
      }
    },
    contarConv(tipo) {
      if (tipo && this.Conv) {
        let count = 0;
        this.Conv.forEach((conv) => {
          if (conv.tipo_conv_comun.tipo_conv_comun_titulo == tipo) {
            count++;
          }
        });
        return count;
      }
    },
    contarCur(tipo) {
      if (tipo && this.Cur) {
        let count = 0;
        this.Cur.forEach((cur) => {
          if (cur.tipo_curso_otro.tipo_conv_curso_nombre == tipo) {
            count++;
          }
        });
        return count;
      }
    },
    dmy(fecha) {
      if (fecha != undefined) {
        const meses = [
          "enero",
          "febrero",
          "marzo",
          "abril",
          "mayo",
          "junio",
          "julio",
          "agosto",
          "septiembre",
          "octubre",
          "noviembre",
          "diciembre",
        ];
        let fechaCadena = fecha.substr(0, 10);
        let fechaArray = fechaCadena.split("-");
        return (
          fechaArray[2] +
          " de " +
          meses[fechaArray[1] - 1] +
          " de " +
          fechaArray[0]
        );
      }
    },
  },
  created() {
    this.$store.commit("loadOn");
    this.getConvocatoriasAll();
    this.getCursosAll();
    this.getServiciosAll();
    this.getOfertasAll();
    this.getPublicaciones();
    this.getGacetaAll();
    this.getEventos();
    this.getVideos();
  },
};
</script>