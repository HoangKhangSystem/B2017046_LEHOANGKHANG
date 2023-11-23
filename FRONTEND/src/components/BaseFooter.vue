<!-- <template>
   <footer id="footer">
      <div class="first-footer">
         <div class="container">
            <div class="d-flex justify-content-between">
               <div class="contact">
                  <h5>Thông tin liên hệ</h5>
                  <ul>
                     <li class="address">
                        <i
                           class="fa-sharp fa-solid fa-location-dot icon-contact"
                        ></i>
                        Đại học Cần Thơ
                     </li>
                     <li class="phone">
                        <i class="fa-solid fa-phone icon-phone"></i>
                        +84 123456789
                     </li>
                     <li class="email">
                        <i class="fa-solid fa-envelope icon-email"></i>
                        123@gmail.com
                     </li>
                  </ul>
               </div>
               <div class="column">
                  <h5>Dịch vụ khách hàng</h5>
                  <ul>
                     <li>
                        <router-link to="/contact">Liên hệ với tôi</router-link>
                     </li>
                     <li>
                        <router-link to="/contact">Về tôi</router-link>
                     </li>
                  </ul>
               </div>
               <div class="column">
                  <h5>Mạng xã hội</h5>
                  <ul>
                     <li>
                        <i class="fa-brands fa-facebook"></i>
                        <a href="https://www.facebook.com"> Facebook</a>
                     </li>
                     <li>
                        <i class="fa-brands fa-twitter"></i>
                        <a href="https://www.twitter.com"> Twitter</a>
                     </li>
                     <li>
                        <i class="fa-brands fa-instagram"></i>
                        <a href="https://www.instagram.com"> Instagram</a>
                     </li>
                  </ul>
               </div>
               <div class="column">
                  <h5>Thanh toán</h5>
                  <ul>
                     <li>
                        <a href="">Trực tiếp</a>
                     </li>
                     <li>
                        <a href="">Chuyển khoản</a>
                     </li>
                  </ul>
               </div>
            </div>
         </div>
      </div>
   </footer>
</template>

<script>
export default {};
</script>

<style scoped>
#footer {
   display: block;
}
.first-footer {
   background-color: #f3f3f3;
   color: #444;
   padding: 20px;
}
#footer h5 {
   font-size: 18px;
   color: #000;
   margin: 0 0 15px 0;
   padding: 0 0 7px 0;
   font-weight: normal;
}
#footer .contact ul {
   list-style: none;
   padding: 0;
}
#footer .contact ul li {
   color: #444;
   text-decoration: none;
   display: block;
   padding: 3px 0;
   line-height: 20px;
   font-size: 14px;
}
#footer .icon-contact {
   margin-right: 5px;
   font-size: 16px;
}
#footer .contact ul li + li {
   margin-top: 12px;
}
#footer .column ul {
   list-style: none;
   padding: 0;
}
#footer .column ul li a {
   color: #888;
   text-decoration: none;
   line-height: 18px;
   font-size: 15px;
}
#footer .column ul li a:hover {
   text-decoration: underline 1px #3e7cb4;
   color: #3e7cb4;
}
</style> -->

<template>
   <footer id="footer">
      <div class="footer-container">
         <div class="footer-section contact-info">
            <h5>Contact Info</h5>
            <ul>
               <li><i class="fa-solid fa-building-columns"></i>Đại học Cần Thơ</li>
               <li><i class="fa-solid fa-envelope icon-email"></i>khang@gmail.com</li>
               <li><i class="fa-solid fa-phone icon-phone"></i>+84 0834667340</li>
               <li><i class="fa-solid fa-map-location-dot"></i>Cần Thơ, Việt Nam</li>

            </ul>
         </div>
         <div class="footer-section customer-service">
            <h5>Customer service</h5>
            <ul>
               <li><router-link to="/contact">Contact-us</router-link></li>
               <li><a href="https://www.goodsmile.info/">Figure website</a></li>
               <li><a href="https://www.amiami.com/eng/">Figure Info</a></li>
               <li><a href="https://www.reddit.com/r/AnimeFigures/">Figure Redit Group</a></li>
            </ul>
         </div>
         <div class="footer-section social-media">
            <h5>Social Media</h5>
            <ul>
               <li><i class="fa-brands fa-facebook"></i><a href="https://www.facebook.com"> Facebook</a></li>
               <li><i class="fa-brands fa-twitter"></i><a href="https://www.twitter.com"> Twitter</a></li>
               <li><i class="fa-brands fa-instagram"></i><a href="https://www.instagram.com"> Instagram</a></li>
            </ul>
         </div>
      </div>
   </footer>
</template>

<script>
export default {};
</script>

<style scoped>
#footer {
   background-color: #ff4;
   color: black;
   padding: 20px;
   text-align: center;
}

.footer-container {
   display: flex;
   justify-content: space-between;
}

.footer-section {
   flex: 1;
   margin: 0 15px;
}

#footer h5 {
   font-size: 18px;
   color: #000;
   margin: 0 0 15px 0;
   padding: 0 0 7px 0;
   font-weight: normal;
}

#footer ul {
   list-style: none;
   padding: 0;
}

#footer ul li {
   color: black;
   text-decoration: none;
   display: block;
   padding: 3px 0;
   line-height: 20px;
   font-size: 14px;
}

#footer .icon-contact {
   margin-right: 5px;
   font-size: 16px;
}

#footer ul li + li {
   margin-top: 12px;
}

#footer ul li a {
   color: black;
   text-decoration: none;
   line-height: 18px;
   font-size: 15px;
}

#footer ul li a:hover {
   text-decoration: underline 1px blue;
   color: blue;
}


</style>
