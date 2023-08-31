<template>
  <!--Site Footer Start-->
  <footer class="site-footer">
          <div class="site-footer-shape wow slideInLeft" data-wow-delay="100ms" data-wow-duration="2500ms"
              style="background-image: url(assets/images/shapes/site-footer-shape.png);">
          </div>
          <div class="site-footer__top">
              <div class="container">
                  <div class="row">
                      <div class="col-xl-3 col-lg-6 col-md-6 wow fadeInUp" data-wow-delay="100ms">
                          <div class="footer-widget__column footer-widget__about">
                              <div class="footer-widget__logo">
                                  <a href="index.html"><img src="assets/images/resources/logo-2.png" alt=""></a>
                              </div>
                              <div class="footer-widget__about-text-box">
                                  <p class="footer-widget__about-text">Redes Sociales</p>
                              </div>
                              <div class="site-footer__social">
                                  <a href="#"><i class="fab fa-twitter"></i></a>
                                  <a href="#"><i class="fab fa-facebook"></i></a>
                                  <a href="#"><i class="fab fa-pinterest-p"></i></a>
                                  <a href="#"><i class="fab fa-instagram"></i></a>
                              </div>
                          </div>
                      </div>
                      <div class="col-xl-3 col-lg-6 col-md-6 wow fadeInUp" data-wow-delay="200ms">
                          <div class="footer-widget__column footer-widget__links clearfix">
                              <h3 class="footer-widget__title">Explorar</h3>
                              <ul class="footer-widget__links-list list-unstyled clearfix">
                                  <li><a href="services.html">Convocatorias</a></li>
                                  <li><a href="dry-cleaning.html">Horarios</a></li>
                                  <li><a href="prices.html">Acreditacion</a></li>
                                  <li><a href="contact.html">Sobre la Carrera</a></li>
                                  <li><a href="contact.html">Ayuda</a></li>
                              </ul>
                          </div>
                      </div>
                      <div class="col-xl-3 col-lg-6 col-md-6 wow fadeInUp" data-wow-delay="300ms">
                          <div class="footer-widget__column footer-widget__contact clearfix">
                              <h3 class="footer-widget__title">Contactos</h3>
                              <p class="footer-widget__contact-text">La Paz - El Alto - Bolivia
                                  Villa Esperanza</p>
                              <ul class="list-unstyled footer-widget__contact-list">
                                  <li>
                                      <div class="icon">
                                          <span class="icon-email"></span>
                                      </div>
                                      <div class="text">
                                          <a href="mailto:needhelp@company.com">edu@gmail.com</a>
                                      </div>
                                  </li>
                                  <li>
                                      <div class="icon">
                                          <span class="icon-telephone"></span>
                                      </div>
                                      <div class="text">
                                          <a href="tel:926668880000"> +591 789 12 123 </a>
                                      </div>
                                  </li>
                              </ul>
                          </div>
                      </div>
                      <!-- <div class="col-xl-3 col-lg-6 col-md-6 wow fadeInUp" data-wow-delay="400ms">
                          <div class="footer-widget__column footer-widget__newsletter clearfix">
                              <h3 class="footer-widget__title">R</h3>
                              <p class="footer-widget__newsletter-text">Escribe aquí</p>
                              <form class="footer-widget__newsletter-form">
                                  <div class="footer-widget__newsletter-input-box">
                                      <input type="email" placeholder="Email Address" name="email">
                                      <button type="submit" class="footer-widget__newsletter-btn">Send</button>
                                  </div>
                              </form>
                          </div>
                      </div> -->
                  </div>
              </div>
          </div>
          <div class="site-footer__bottom">
              <div class="container">
                  <div class="row">
                      <div class="col-xl-12">
                          <div class="site-footer__bottom-inner">
                              <p class="site-footer__bottom-text">©  <a href="#">#</a>
                              </p>
                              <ul class="list-unstyled site-footer__bottom-menu">
                                  <li><a href="about.html">&</a></li>
                                  <li><span>/</span></li>
                                  <li><a href="about.html">Privacy Policy</a></li>
                              </ul>
                          </div>
                      </div>
                  </div>
              </div>
          </div>
      </footer>
      <!--Site Footer End-->
</template>

<script>
import { mapState } from "vuex";
export default {
  name: "footerView",
  computed: {
    ...mapState(["Institucion", "MenuConv", "MenuCur", "url_api"]),
  },
  methods: {},
};
</script>