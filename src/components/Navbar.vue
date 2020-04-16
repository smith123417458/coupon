<template>

<div>

  <nav
    class="navbar navbar-expand-xl p-0 fixed-top navDefault"
    :class="{ navActive }"
    @mouseenter="navMouseEnter"
    @mouseleave="navMouseLeave"
  >
    <a class="navbar-brand" href="#">
      <img
        src="../assets/img/r02.png"
        width="30"
        height="30"
        class="d-inline-block  align-top ml-4"
      />
    
    </a>
    <div class="collapse navbar-collapse ml-xl-6 order-2 order-xl-1">
      <ul class="navbar-nav">
        <li class="nav-item">
         
        </li>
   
        <li class="nav-item d-none d-xl-block">
         
        </li>
      </ul>
    </div>
    <!-- 會員登入 -->
    <ul class="navbar-nav mr-xl-6 order-1 order-xl-2">
      <li class="nav-item">
        <router-link class=" d-block py-3 px-4" to="/signin">
          <img src="../assets/img/log-in.png" />
        </router-link>
      </li>
    
      

     
    </ul>

    

   
    



  </nav>





  </div>

</template>

<script>
import { mapGetters, mapActions } from "vuex";
import { gsap } from "gsap";
export default {
  data() {
    return {
      navHeight: 0,
      navActive: false
    };
  },
  computed: {
    getcar() {
      return this.$store.state.carts.carts.length;
    },
    ...mapGetters("favoriteModules", ["favorites", "favoritesLength"])
  },
  watch: {
    $route() {
      const vm = this;
      const { path } = this.$route;
  
      if (path !== "/") {
        vm.$bus.$emit("goTop");
      }
     
      $("#brand-list").slideUp();

      if (path !== "/" && path !== "/product") {
        vm.navActive = true;
      } else {
        vm.navActive = false;
      }
    },

    getcar() {
      gsap.from("#cart", 0.9, {
        scale: 8
      });
    }

  },
  methods: {
   
    
    
    changeCategory(selectedCategory) {
      const vm = this;
      vm.$store.dispatch("changeCategory", selectedCategory).then(() => {
        if (vm.$route.path !== "/product") {
          vm.$router.push("/product");
        }
   
      });
    },

    
  },
  created() {
    window.addEventListener("scroll", this.windowScroll, false);
    this.$store.dispatch("getCarts");
    this.$store.dispatch("favoriteModules/getFavorite");
  }
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/customMixins.scss";

// navbar 預設樣式

.navbar-nav{
  flex-direction: row;
}
.navDefault {
  a,
  .navbar-nav a {
    color: white;
  }
  transition: all 0.5s;
}

// 當畫面滾動、或在非首頁、/product 路由時為黑字白底
.navActive {
  a,
  .nav-item a {
    color: black;
  }
  background: white;
  @include box-shadow;
}

#brand-list {
  display: none;

  @include BS-xl {
    display: none;
  }
}

#brand-list-rwd {
  display: none;
}

@media (max-width:501px) {
  #mark{
    display: none;
  }
}

// ================================================================================
.dropdown-menu {
  z-index: 9999;
}

.favorite {
  float: right;
  margin-left: 0.25rem;
}

.favorite-btn {
  float: right;
  position: relative;
  background-color: transparent;
  text-align: right;
  font-size: inherit;
  .badge {
    position: absolute;
    top: auto;
    bottom: 2px;
    right: -1px;
  }
}
.favorite-list {
  &:hover,
  &:active {
    background-color: rgb(0, 98, 255);
    text-decoration: underline;
  }
  .favorite-list-delbtn:hover,
  .favorite-list-delbtn:active {
    i {
      font-size: 1.25rem;
    }
  }
}
</style>
