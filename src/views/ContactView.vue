<template>
  <div>
    <div class="page-title-area bg-overlay bg-overlay-img banner-img">
      <div class="container">
        <div class="row">
          <div class="col-lg-7">
            <div class="breadcrumb-inner">
              <h2 class="page-title">CONTACTASE CON NOSOTROS</h2>
              <ul class="page-list">
                <li><router-link to="/">INICIO</router-link></li>
                <li>CONTACTO</li>
              </ul>
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
          <div class="col-lg-4 bg-gray">
            <div class="section-title">
              <h2 class="title">Contactase con nosotros</h2>
            </div>
          </div>
          <div class="col-lg-8">
            <div class="content bg-gray">
              <p>
                <b><i class="fa fa-phone"></i> Celular 1: </b>
                {{ Institucion.institucion_celular1 }}
              </p>
              <p>
                <b><i class="fa fa-phone"></i> Celular 2: </b>
                {{ Institucion.institucion_celular2 }}
              </p>
              <p>
                <b><i class="fa fa-phone"></i> Telefono 1: </b>
                {{ Institucion.institucion_telefono1 }}
              </p>
              <p>
                <b><i class="fa fa-phone"></i> Telefono 2: </b>
                {{ Institucion.institucion_telefono2 }}
              </p>
              <p>
                <b><i class="fa fa-envelope"></i> Correo 1: </b>
                {{ Institucion.institucion_correo1 }}
              </p>
              <p>
                <b><i class="fa fa-envelope"></i> Correo 2: </b>
                {{ Institucion.institucion_correo2 }}
              </p>
              <p>
                <b><i class="fa fa-facebook"></i> Facebook: </b>
                <a :href="Institucion.institucion_facebook" target="_blank">
                  {{ Institucion.institucion_facebook }}
                </a>
              </p>
              <p>
                <b><i class="fa fa-twitter"></i> Twitter: </b>
                <a :href="Institucion.institucion_twitter" target="_blank">
                  {{ Institucion.institucion_twitter }}
                </a>
              </p>
              <p>
                <b><i class="fa fa-youtube"></i> Youtube: </b>
                <a :href="Institucion.institucion_youtube" target="_blank">
                  {{ Institucion.institucion_youtube }}
                </a>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="contact-g-map">
      <h2>O visítenos</h2>
      <h4>
        <i class="fa fa-map-marker"></i> {{ Institucion.institucion_direccion }}
      </h4>
      <iframe :src="Institucion.institucion_api_google_map"></iframe>
    </div>
  </div>
</template>

<style scoped>
.content {
  font-size: 1.2em;
}
</style>

<script>
import { mapState } from "vuex";
export default {
  name: "contanctView",
  computed: {
    ...mapState(["url_api", "Institucion"]),
  },
  // created() {
  //   this.$store.commit("loadOn");
  // },
  // mounted() {
  //   this.$store.commit("loadOn");
  // },
};
</script>