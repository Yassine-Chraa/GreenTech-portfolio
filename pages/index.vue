<template>
  <div>
    <div class="fixed-top" style="background-color: #fff">
      <b-navbar
        toggleable="md"
        type="light"
        variant="light"
        style="font-size: 14px; font-weight: 700"
        class="container-lg"
      >
        <b-navbar-brand href="#"
          ><span style="color: rgb(196, 151, 151)">GREEN</span
          >TECH</b-navbar-brand
        >

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto" style="text-transform: uppercase">
            <b-nav-item to="#header" active>Acceuil</b-nav-item>
            <b-nav-item href="#about">A propos</b-nav-item>
            <b-nav-item href="#produits">Nos Produits</b-nav-item>
            <b-nav-item href="#contact">Contact</b-nav-item>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
    <b-container id="header" fluid="lg">
      <b-row
        :style="{
          height: height + 'px',
          alignContent: 'center',
          paddingTop: '56px',
        }"
      >
        <b-col :cols="width > 400 ? 7 : 12"
          ><div style="padding-top: 48px">
            <h1 class="heading" style="font-size: 2.5em">
              GREENTECH CONSULTING
            </h1>
            <p class="text">
              Bureau d'etude import et export marchand de produits
              phytosantaires.
            </p>
            <b-btn href="#contact" class="link">Nous contacter</b-btn>
          </div>
        </b-col>
        <b-col v-if="width > 400" cols="5" class="bg">
          <b-img src="~/assets/img/bg.png" thumbnail style="border: unset" />
        </b-col>
      </b-row>
    </b-container>
    <div class="main">
      <b-container fluid="lg">
        <b-row id="about">
          <b-col cols="12" md="6">
            <b-img
              src="~/assets/img/about-1.webp"
              thumbnail
              style="border-radius: 50%"
            ></b-img>
            <b-img
              v-if="width > 767"
              src="~/assets/img/about-2.webp"
              thumbnail
              class="img-float"
            ></b-img>
          </b-col>
          <b-col cols="12" md="6"
            ><div style="padding-top: 48px; padding-left: 16px">
              <h2>A PROPOS</h2>
              <h3>Produits phytosantaires</h3>
              <p class="p-style1">
                GREENTECH is the largest global organic farm.
              </p>
              <p style="font-weight: 500; opacity: 0.7">
                There are many variations of passages of lorem ipsum available
                but the majority have suffered alteration in some form by
                injected humor or random word which don’t look even.
              </p>
              <!--<b-btn href="#" class="link">Découvrir plus</b-btn>-->
            </div></b-col
          >
        </b-row>
        <div id="produits">
          <div style="padding-bottom: 32px; text-align: center">
            <h2>Produits</h2>
            <h3>Explorer les produits</h3>
          </div>
          <VueSlickCarousel v-bind="settings">
            <div class="produit" v-for="(produit, ind) in produits" :key="ind">
              <div class="card">
                <div class="card-body">
                  <h4 class="card-title">{{ produit.nom }}</h4>
                  <p class="card-text">
                    {{ produit.desc }}
                  </p>
                </div>
                <div>
                  <b-badge class="categorie">230DH</b-badge>
                  <div>
                    <img
                      class="card-img-bottom"
                      :src="require('~/assets/img/'+produit.img)"
                      alt="Card image cap"
                    />
                  </div>
                </div>
              </div>
            </div>
          </VueSlickCarousel>
        </div>
        <!--<b-row id="services">
          <b-col cols="12" style="padding-bottom: 32px; text-align: center">
            <h2>Services</h2>
            <h3>Ce que nous offrons</h3>
          </b-col>
          <b-row style="width: 100%">
            <b-col v-for="(service,ind) in services" :key="ind" sm="6" lg="4" class="col-xs-12">
              <div class="card service">
                <img
                  class="card-img-top"
                  :src="require('~/assets/img/'+service.img)"
                  alt="Card image cap"
                />
                <div class="card-body">
                  <fa
                    :icon="['fa-solid', service.icon]"
                    class="service-icon"
                  />
                  <h4 class="card-title">{{service.nom}}</h4>
                </div>
              </div>
            </b-col>
          </b-row>
        </b-row>-->
        <b-row id="contact">
          <b-col cols="12" md="5">
            <h2>Contact</h2>
            <h3>Laissez un message</h3>
            <p>
              Curabitur mollis bibendum luctus. Duis suscipit vitae dui sed
              suscipit.Curabitur mollis bibendum luctus. Duis suscipit vitae dui
              sed suscipit.
            </p>
            <ul>
              <li>
                <fa :icon="['fa-solid', 'phone']" style="margin-right: 16px" />
                <span>0664142715</span>
              </li>
              <li>
                <fa
                  :icon="['fa-solid', 'envelope']"
                  style="margin-right: 16px"
                />
                <span>yassine.chraa@gmail.com</span>
              </li>
              <li>
                <fa
                  :icon="['fa-solid', 'location-dot']"
                  style="margin-right: 16px"
                />
                <span>201 Oak Street Building 27 Manchester, USA</span>
              </li>
            </ul>
          </b-col>
          <b-col cols="12" md="7">
            <h4></h4>
            <b-form>
              <b-row>
                <b-col cols="12" sm="6">
                  <b-form-input
                    type="text"
                    placeholder="Nom complete"
                    v-model="form.nom"
                  />
                </b-col>
                <b-col cols="12" sm="6"
                  ><b-form-input
                    type="text"
                    placeholder="Contact No:"
                    v-model="form.numero"
                /></b-col>
              </b-row>
              <b-row>
                <b-col cols="12" sm="6">
                  <b-form-input
                    type="text"
                    placeholder="email"
                    v-model="form.email"
                  />
                </b-col>
                <b-col cols="12" sm="6"
                  ><b-form-input
                    type="text"
                    placeholder="Sujet"
                    v-model="form.sujet"
                /></b-col>
              </b-row>
              <b-row>
                <b-col cols="12"
                  ><b-textarea
                    placeholder="Message"
                    rows="5"
                    no-resize
                    v-model="form.contenu"
                  ></b-textarea
                ></b-col>
              </b-row>
              <b-btn type="button" @click="sendMessage()"> Envoyer</b-btn>
            </b-form>
          </b-col>
        </b-row>
      </b-container>
    </div>
    <div class="map">
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d424462.7700065688!2d-5.385850865605617!3d33.783518250745516!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd9f81afa78bfa91%3A0xd70cd1c9185d4d88!2sAl%20Hadika!5e0!3m2!1sfr!2sma!4v1660155573322!5m2!1sfr!2sma"
        :height="width > 575 ? 400 : 350"
        style="border: 0; width: 100%"
        allowfullscreen=""
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade"
      ></iframe>
    </div>
    <div class="footer">
      <b-container fluid="md">
        <b-row>
          <b-col cols="4" sm="3">
            <ul class="social-media">
              <li>
                <a href="#"><fa :icon="['fa-brands', 'facebook-f']" /></a>
              </li>
              <li>
                <a href=""> <fa :icon="['fa-brands', 'whatsapp']" /></a>
              </li>
              <li>
                <a href=""> <fa :icon="['fa-brands', 'instagram']" /></a>
              </li>
              <li>
                <a href=""> <fa :icon="['fa-brands', 'linkedin-in']" /></a>
              </li></ul
          ></b-col>
          <b-col cols="8" sm="9"
            ><p style="font-weight: 600">
              © 2022 GREENTECH. made with love by YassineChraa
            </p></b-col
          >
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      settings: {
        lazyLoad: 'ondemand',
        focusOnSelect: true,
        infinite: true,
        speed: 1000,
        slidesToShow: 4,
        slidesToScroll: 4,
        touchThreshold: 4,
        autoplay: true,
        responsive: [
          {
            breakpoint: 1200,
            settings: {
              slidesToShow: 3,
              slidesToScroll: 3,
              initialSlide: 3,
            },
          },
          {
            breakpoint: 767,
            settings: {
              slidesToShow: 2,
              slidesToScroll: 2,
              initialSlide: 2,
            },
          },
          {
            breakpoint: 480,
            settings: {
              slidesToShow: 1,
              slidesToScroll: 1,
              initialSlide: 1,
            },
          },
        ],
      },
      width: 0,
      height: 600,
      form: {
        nom: '',
        numero: '',
        email: '',
        sujet: '',
        contenu: '',
      },
      produits: [
        {
          nom: 'MIX EXPERT',
          desc: 'MIX EXPERT est un produit à base de micro-éléments spécifiques, résout les carences en nutriments',
          img: 'mix-expert.jpeg'
        },
        {
          nom: 'CALEXPERT',
          desc: 'CALEXPERT EST formulé pour résoudre les carences en calcium dans tous les types de cultures',
          img: 'cal-expert.jpeg'
        },
        {
          nom: 'K35 EXPERT',
          desc: 'K35 EXPERT est un fertilisant solide a base de potassium développé pour favoriser la maturation homogène des fruits',
          img: 'k35-expert.jpeg'
        },
        {
          nom: 'TERRA EXPERT',
          desc: 'TERRA EXPERT est un produit à base de potassium, résout les carences dans le macronutriment de potassium',
          img: 'terra-expert.jpeg'
        },
        {
          nom: 'GROW UP EXPERT',
          desc: 'GROW UP EXPERT est un fertilisant mineral a base du calcium.Il peut etre appliqué à la fois en mode foliare ou par irrigation',
          img: 'grow-expert.jpeg'
        },
        {
          nom: 'KOLOR EXPERT',
          desc: 'KOLOR EXPERT est un produit à base de potassium extrement efficace qui permet son absorption et sa distribution immédiates',
          img: 'kolor-expert.jpeg'
        },

        {
          nom: 'ROW EXPERT',
          desc: 'ROW EXPERT est un produit pour les cultures extensives pour lutter contre tout type de stress environnemental',
          img: 'row-expert.jpeg'
        },
      ],
    }
  },
  methods: {
    sendMessage() {
      this.$axios
        .post('http://127.0.0.1:8000/api/messages', this.form)
        .then((res) => {})
    },
  },
  mounted() {
    this.width = window.innerWidth
    window.addEventListener('resize', () => {
      this.width = window.innerWidth
    })
    this.height = window.innerHeight
    window.addEventListener('resize', () => {
      this.height = window.innerHeight
    })
  },
}
</script>
<style></style>
