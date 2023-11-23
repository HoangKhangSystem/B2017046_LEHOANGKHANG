<template>
   <div class="container">
      <nav class="navbar navbar-expand-lg">
         <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
         </button>

         <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
               <li class="nav-item active">
                  <router-link to="/home" class="nav-link">
                     <i class="fa-solid fa-house"></i>
                  </router-link>
               </li>
               <li class="nav-item">
                  <router-link to="/contact" class="nav-link">
                     Contact
                     <i class="fa-solid fa-messages"></i>
                  </router-link>
               </li>
               <li class="nav-item">
                  <router-link to="/cart" class="nav-link">
                     <i class="fa-solid fa-cart-shopping"></i>
                  </router-link>
               </li>
               <li class="nav-item count_products-cart">
                  <router-link to="/cart">
                     {{ localCarts.length }}
                  </router-link>
               </li>
               <li class="nav-item user_name" v-if="this.localUser.role != ''">
                  <router-link to="/" class="nav-link" @click="handleLogout">
                     <b class="user-name">Hello {{ this.localUser.name }}</b>
                     <button class="btn btn-danger logout-btn">
                        <i class="fa-solid fa-right-from-bracket"></i>
                        Logout
                     </button>
                  </router-link>
               </li>
               <li class="nav-item" v-if="this.localUser.role === 'admin'">
                  <router-link to="/admin" class="nav-link">
                     <button class="btn btn-primary admin-btn">
                        <i class="fa-solid fa-people-roof"></i>
                     </button>
                  </router-link>
               </li>
            </ul>
         </div>
      </nav>
   </div>
</template>

<script>
export default {
   data() {
      return {
         localUser: {},
         localCarts: {},
      };
   },
   methods: {
      handleLogout() {
         localStorage.removeItem("localUserLogin");
      },
   },
   mounted() {
      const user = JSON.parse(localStorage.getItem("localUserLogin"));
      this.localUser = user;
      const localProductCart = JSON.parse(
         localStorage.getItem("localProductCart") ?? "[]"
      );
      this.localCarts = localProductCart;
   },
};
</script>

<style>
.container {
   justify-content: center;
}
.container-fluid {
   padding: 0 0;
}
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #ff4;
}
.navbar .nav-item {
   position: relative;
   text-align: center;
}
.navbar .nav-item a {
  font-weight: bold;
  font-family: "Open Sans", sans-serif;
  color: black !important;
  text-align: center;
  font-size: 20px;
}
.navbar .nav-item a:hover {
   text-decoration: underline 1px blue;
   color: #0088ff !important;
}
.nav-item ul li a {
   display: flex;
   text-align: center;
}
.dropdown-menu {
   width: 100px;
   display: none;
   position: absolute;
   background: #fff;
   z-index: 1;
   border-top: 3px solid #3e7cb4;
   border-bottom: 0 none;
   border-left: 0 none;
   border-right: 0 none;
   font-size: 16px;
   padding: 10px 0;
   margin-top: 0;
   margin-left: -34px;
   border-radius: 0%;
}
.dropdown-menu ul {
   position: relative;
   z-index: 500;
   left: -15px;
   right: 0;
   list-style: none;
   margin-left: 0;
}
.nav-item:hover .dropdown-menu {
   display: block;
}
.user_name {
   margin-left: 700px;
   text-transform: uppercase;
}

.user-name {
   font-weight: bold;
   font-size: 18px;
   color: black;
   text-align: center;
}

.logout-btn {
   width: 70px;
   height: 70px;
   border-radius: 50%;
   background-color: #dc3545;
   color: #fff;
   border: none;
   /* display: flex; */
   align-items: center;
   cursor: pointer;
}
.logout-btn:hover {
   background-color: #bd2130;
}
.logout-btn i {
   margin-right: 0px;
}
.admin-btn {
   width: 30px;
   height: auto;
   padding: 0px !important;
   margin-top: -5px;
}
.count_products-cart {
   left: -5px;
   top: 8px;
}
</style>
