<script setup>
import { onMounted, onUnmounted } from "vue";

//example components
import NavbarDefault from "../../examples/navbars/NavbarDefault.vue";
import DefaultFooter from "../../examples/footers/FooterDefault.vue";
import Header from "../../examples/Header.vue";

// components
import MaterialInput from "../../components/MaterialInput.vue";

//images
import mainBg from "@/assets/img/main/coolbackgrounds-gradient-cool.png";
import wavesWhite from "@/assets/img/waves-white.svg";

//appStore
import { useAppStore } from "@/stores/index.js";
const appStore = useAppStore();

// input 제어를 위한 import
import setMaterialInput from "@/assets/js/material-input";

//hooks
const body = document.getElementsByTagName("body")[0];
onMounted(() => {
  body.classList.add("presentation-page");
  body.classList.add("bg-gray-200");
  setMaterialInput();
});
onUnmounted(() => {
  body.classList.remove("presentation-page");
  body.classList.remove("bg-gray-200");
});
</script>

<template>
  <!-- NavBar -->
  <div class="container position-sticky z-index-sticky top-0">
    <div class="row">
      <div class="col-12">
        <NavbarDefault
          :sticky="true"
          :action="{
            route: '/login',
            label: 'Login',
            color: 'bg-gradient-success',
          }"
        />
      </div>
    </div>
  </div>
  <!--// NavBar -->

  <!-- Header -->
  <Header>
    <div
      class="page-header min-vh-55"
      :style="`background-image: url(${mainBg})`"
      loading="lazy"
    >
      <div class="container">
        <div class="row">
          <div class="col-lg-7 text-center mx-auto position-relative">
            <h1
              class="text-dart pt-3 mt-n5 me-2"
              :style="{ display: 'inline-block ' }"
            >
              {{ appStore.siteTitle }}
            </h1>
            <p class="lead text-dart px-5 mt-3" :style="{ fontWeight: '500' }">
              Your simple and powerful URL shortener.<br />Turn long, messy links into clean, shareable URLs in seconds.
            </p>
          </div>
        </div>
      </div>
    </div>
  </Header>
  <!--// Header -->

  <!-- Contents -->
  <div class="card card-body blur shadow-blur mx-3 mx-md-4 mt-n6">
    <div
      class="container-fluid mt-sm-5 border-radius-xl"
      :style="{
        background: 'linear-gradient(195deg, rgb(66, 66, 74), rgb(25, 25, 25))'
      }"
    >
      <div
        class="page-header py-6 py-md-5 my-sm-3 mb-3 border-radius-xl"
        :style="{
          backgroundImage: `url(${wavesWhite})`
        }"
        loading="lazy"
      >
        <span class="mask bg-gradient-dark"></span>
        <div class="container">
          <div class="row">
            <div class="d-flex justify-content-center p-5">
              <div class="col-lg-8 ms-lg-5 text-center">
                <h3 class="text-white">Paste your link below & Shorten It!</h3>
                
                <MaterialInput
                  class="input-group-outline mb-4"
                  :label="{ text: 'url', class: 'form-label' }"
                  type="text"
                  inputClass="text-white"
                />
                
                <a class="btn btn-sm mb-0 bg-gradient-success px-5 py-3 mt-4">
                  Get Your Shortened Link
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- Contents -->

  <!-- Footer -->
  <DefaultFooter />
  <!--// Footer -->
</template>
