<template>
  <div>
    <div class="widget widget_catagory">
      <h4 class="widget-title">Categorías</h4>
      <ul class="catagory-items">
        <li v-for="(conv, id_conv) of MenuConv" :key="id_conv">
          <router-link
            :to="'/convocatorias/' + conv.idtipo_conv_comun"
            @click="$store.commit('clickLink')"
          >
            <i class="fa fa-angle-right"></i>
            {{ conv.tipo_conv_comun_titulo[0].toUpperCase()
            }}{{ conv.tipo_conv_comun_titulo.substr(1).toLowerCase() }}
          </router-link>
        </li>
        <li v-for="(cur, id_cur) of MenuCur" :key="id_cur">
          <router-link
            :to="'/cursos/' + cur.idtipo_curso_otros"
            @click="$store.commit('clickLink')"
          >
            <i class="fa fa-angle-right"></i>
            {{ cur.tipo_conv_curso_nombre[0].toUpperCase()
            }}{{ cur.tipo_conv_curso_nombre.substr(1).toLowerCase() }}
          </router-link>
        </li>
        <li>
          <router-link to="/servicios" @click="$store.commit('clickLink')">
            <i class="fa fa-angle-right"></i> Servicios
          </router-link>
        </li>
        <li>
          <router-link to="/ofertas" @click="$store.commit('clickLink')">
            <i class="fa fa-angle-right"></i> Ofertas académicas
          </router-link>
        </li>
        <li>
          <router-link to="/publicaciones" @click="$store.commit('clickLink')">
            <i class="fa fa-angle-right"></i> Publicaciones
          </router-link>
        </li>
        <li>
          <router-link to="/gaceta" @click="$store.commit('clickLink')">
            <i class="fa fa-angle-right"></i> Gaceta
          </router-link>
        </li>
        <li>
          <router-link to="/eventos" @click="$store.commit('clickLink')">
            <i class="fa fa-angle-right"></i> Eventos
          </router-link>
        </li>
        <li>
          <router-link to="/videos" @click="$store.commit('clickLink')">
            <i class="fa fa-angle-right"></i> Videos
          </router-link>
        </li>
      </ul>
    </div>
    <hr />

    <div class="widget widget_tags">
      <h4 class="widget-title">Tags</h4>
      <div class="tagcloud">
        <a
          :href="link.ei_link"
          target="_blank"
          v-for="(link, id_link) of Links"
          :key="id_link"
          :title="link.ei_tipo"
          >{{ link.ei_nombre }}</a
        >
        <a href="https://sie.upea.bo/" target="_blank">SIE UPEA</a>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "SidebarCustom",
  computed: {
    ...mapState(["MenuConv", "MenuCur", "Links"]),
  },
  methods: {
    clickBack() {
      this.$store.commit("clickLink");
      this.$router.go(-1);
    },
  },
};
</script>