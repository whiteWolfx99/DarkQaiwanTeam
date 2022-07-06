<template>
  <v-app>

    <!-- User  -->

      <nav
        class="navbar navbar-expand-lg navbar-light bg-light"
        v-if="$session.get('role') == 'Admin'"
      >
        <div class="container-fluid">
            <router-link
                  class="nav-link active"
                  aria-current="page"
                  to="/Home"
                  > <img
            src="assets\Artboard1.png"
            alt="Italian Trulli"
            style="width: 180px; height: auto"
          /></router-link>
         

          <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon">
               
            </span>
          </button>
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <v-btn
                v-on:click="enc"
                class="nav-link"
          dark
                >Encrypt_Data</v-btn
              >
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
             
            </ul>
            <form class="d-flex">
              <!-- <v-btn style="margin-right: 20px" v-on:click="StoreBook"
                ><i dark class="fa-solid fa-store"></i
              ></v-btn> -->

              <v-btn
                v-on:click="logout"
                v-if="$session.get('id')"
                class="nav-link"
                dark
                >Sign-out</v-btn
              >
            </form>
          </div>
        </div>
      </nav>

    

 <!-- User  -->

      <nav
        class="navbar navbar-expand-lg navbar-light bg-light"
        v-if="$session.get('role') == 'User'"
      >
        <div class="container-fluid">
            <img
            src="assets\Artboard1.png"
            alt="Italian Trulli"
            style="width: 180px; height: auto"
          />
         

          <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon">
               
            </span>
          </button>
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
        
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
             
            </ul>
            <form class="d-flex">
              <!-- <v-btn style="margin-right: 20px" v-on:click="StoreBook"
                ><i dark class="fa-solid fa-store"></i
              ></v-btn> -->

              <v-btn
                v-on:click="logout"
                v-if="$session.get('id')"
                class="nav-link"
                dark
                >Sign-out</v-btn
              >
            </form>
          </div>
        </div>
      </nav>

      <router-view />

     
   



    
  </v-app>
</template>

<script>
export default {
  name: "App",
  methods: {

    enc() {
       this.$router.push({ path: "/UserCry" });
    },
    logout() {
      this.$session.destroy();
      this.$router.push({ path: "/" });
    },

   
  },

  data: () => ({
    drawer: false,
    group: null,
  }),
};
</script>
