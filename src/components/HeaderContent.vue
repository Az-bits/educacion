<template>
    <nav class="main-menu clearfix">
        <div class="main-menu-wrapper clearfix">
            <div class="main-menu-wrapper__left" style="padding: 19px 0;">
                <div class="main-menu-wrapper__logo">
                    <router-link to="/" class="d-flex align-items-center">
                        <img :src="url_api + '/InstitucionUpea/' + Institucion.institucion_logo
                            " alt="img" width="70" height="70" />
                        &nbsp;
                        <h3>{{ Institucion.institucion_nombre }}</h3>
                    </router-link>
                </div>
            </div>
            <div class="main-menu-wrapper__right">
                <div class="main-menu-wrapper__main-menu">
                    <a href="" class="mobile-nav__toggler"><i class="fa fa-bars"></i></a>
                    <ul class="main-menu__list">
                        <li class="dropdown current">
                            <router-link to="/">Inicio</router-link>
                        </li>
                        <li class="dropdown">
                            <a href="#">Sobre la Carrera</a>
                            <ul>
                                <li><router-link to="/carreramision">Misión</router-link></li>
                                <li><router-link to="/carreravision">Visión</router-link></li>
                                <li><router-link to="/carreraobjetivos">Objetivos</router-link></li>
                                <li><router-link to="/">Historia</router-link></li>

                            </ul>
                        </li>
                        <li class="dropdown">
                            <a href="#">Ofertas Academicas</a>
                            <ul>
                                <li><router-link to="/">Perfil Profesional</router-link></li>
                                <li><router-link to="/">Sedes Academicas</router-link></li>
                                <li><router-link to="/">Cursos</router-link></li>
                                <li><router-link to="/">Convocatorias</router-link></li>
                            </ul>
                        </li>
                        <li class="dropdown">
                            <a href="#">IICCE</a>
                            <ul>
                                <li><router-link to="/">Modalidades de Titulación</router-link></li>
                                <li><router-link to="/">Modalidades de Graduación</router-link></li>
                                <li><router-link to="/">Reglamento</router-link></li>
                            </ul>
                        </li>
                        <li class="dropdown">
                            <a href="#">Kardex</a>
                            <ul>
                                <li><router-link to="/">Plan de Estudios</router-link></li>
                                <li><router-link to="/horario">Horarios</router-link></li>
                                <li><router-link to="/">Turnos</router-link></li>
                            </ul>
                        </li>
                        <li class="dropdown">
                            <a href="#">Acreditación</a>
                            <ul>
                                <li><router-link to="/estatutoceub">Estatuto CEUB</router-link></li>
                                <li><router-link to="/estatutoupea">Estatuto UPEA</router-link></li>
                                <li><router-link to="/resolucioncongreso">Resolucion Congreso
                                        UPEA</router-link></li>
                                <li><router-link to="/certificacionbo">Resolución Certificación a Nivel
                                        Nacional</router-link></li>
                                <li><router-link to="/certificacionceub">Resolución Certificación
                                        CEUB</router-link></li>
                                <li><router-link to="/pdi2017">PDEI - UPEA 2017 a 2021</router-link></li>
                                <li><router-link to="/pdi2021">PDEI - UPEA DEL 2021 - 2025</router-link>
                                </li>
                                <li><router-link to="/pdice2021">PDEI de la carrera del Area de Educación
                                        2017 2021</router-link></li>
                                <li><router-link to="/pdice">PDEI Carrera Ciencias de la
                                        Educación</router-link></li>
                                <li><router-link to="/mof">Manuales de Organizacion - MOF</router-link></li>
                                <li><router-link to="/"></router-link></li>
                            </ul>
                        </li>
                        <li class="dropdown">
                            <a href="#">Links</a>
                            <ul>
                                <li><a href="https://virtualeducacion.upea.bo/">Plataforma Virtual</a></li>
                                <li><a href="https://inscripcioneseducacion.upea.bo/">Inscripciones UPEA</a>
                                </li>
                                <li><a href="https://biblioteca.upea.bo/">Biblioteca Virtual</a></li>
                            </ul>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </nav>
</template>
<script>
import { mapState } from "vuex";
export default {
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