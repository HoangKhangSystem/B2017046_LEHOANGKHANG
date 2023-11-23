<template>
   <!-- <div class="container">
      <div class="d-flex justify-content-center h-100">
         <div class="card">
            <div class="card-header text-center">
               <h3>Đăng ký tài khoản</h3>
            </div>
            <div class="card-body">
               <form @submit.prevent="register()">
                  <div class="input-group form-group">
                     <div class="input-group-prepend">
                        <span class="input-group-text">
                           <i class="fa-solid fa-user"></i>
                        </span>
                     </div>
                     <input
                        type="text"
                        class="form-control"
                        placeholder="Họ và tên"
                        @blur="validate()"
                        v-model="user.name"
                        :class="{ 'is-invalid': errors.name }"
                     />
                     <div class="invalid-feedback" v-if="errors.name">
                        {{ errors.name }}
                     </div>
                  </div>
                  <div class="input-group form-group">
                     <div class="input-group-prepend">
                        <span class="input-group-text">
                           <i class="fa-solid fa-envelope"></i>
                        </span>
                     </div>
                     <input
                        type="email"
                        class="form-control"
                        placeholder="Email"
                        @blur="validate()"
                        v-model="user.email"
                        :class="{ 'is-invalid': errors.email }"
                     />
                     <div class="invalid-feedback" v-if="errors.email">
                        {{ errors.email }}
                     </div>
                  </div>
                  <div class="input-group form-group">
                     <div class="input-group-prepend">
                        <span class="input-group-text">
                           <i class="fas fa-key"></i>
                        </span>
                     </div>
                     <input
                        type="password"
                        class="form-control"
                        placeholder="Mật khẩu"
                        @blur="validate()"
                        v-model="user.password"
                        :class="{ 'is-invalid': errors.password }"
                     />
                     <div class="invalid-feedback" v-if="errors.password">
                        {{ errors.password }}
                     </div>
                  </div>
                  <div class="input-group form-group">
                     <div class="input-group-prepend">
                        <span class="input-group-text">
                           <i class="fa-solid fa-shield"></i>
                        </span>
                     </div>
                     <input
                        type="password"
                        class="form-control"
                        placeholder="Nhập lại mật khẩu"
                        @blur="validate()"
                        v-model="user.repassword"
                        :class="{ 'is-invalid': errors.repassword }"
                     />
                     <div class="invalid-feedback" v-if="errors.repassword">
                        {{ errors.repassword }}
                     </div>
                  </div>
                  <div class="form-group">
                     <input
                        type="submit"
                        value="Đăng ký"
                        class="btn login_btn"
                     />
                  </div>
               </form>
            </div>
            <div class="card-footer">
               <div class="d-flex justify-content-center links">
                  <p>
                     Đăng nhập ngay!
                     <router-link to="/">ĐĂNG NHẬP</router-link>
                  </p>
               </div>
            </div>
         </div>
      </div>
   </div> -->

   <div class="background">
        <div class="shape"></div>
        <div class="shape"></div>
    </div>
    <form @submit.prevent="register()">
        <h3>Đăng Ký</h3>

        <label for="username">Username</label>
                     <input
                        type="text"
                        class="form-control"
                        placeholder="Họ và tên"
                        @blur="validate()"
                        v-model="user.name"
                        :class="{ 'is-invalid': errors.name }"
                     />
      <label for="email">Email</label>
                     <input
                        type="email"
                        class="form-control"
                        placeholder="Email"
                        @blur="validate()"
                        v-model="user.email"
                        :class="{ 'is-invalid': errors.email }"
                     />
        <label for="password">Password</label>
                     <input
                        type="password"
                        class="form-control"
                        placeholder="Mật khẩu"
                        @blur="validate()"
                        v-model="user.password"
                        :class="{ 'is-invalid': errors.password }"
                     />
         <label for="password">ConfirmPassword</label>
                     <input
                        type="password"
                        class="form-control"
                        placeholder="Nhập lại mật khẩu"
                        @blur="validate()"
                        v-model="user.repassword"
                        :class="{ 'is-invalid': errors.repassword }"
                     />
        <button>Đăng Ký</button>
        <!-- <div class="social">
          <div class="go"><i class="fab fa-google"></i>  Google</div>
          <div class="fb"><i class="fab fa-facebook"></i>  Facebook</div>
        </div> -->
        <div class="card-footer">
               <div class="d-flex justify-content-center links">
                  <p>
                     Bạn đã có tài khoản?
                     <router-link to="/">ĐĂNG NHẬP</router-link>
                  </p>
               </div>
            </div>
    </form>
</template>

<script>
import UserService from "../services/user.service";

export default {
   data() {
      return {
         errors: {
            name: "",
            email: "",
            password: "",
            repassword: "",
         },
         user: {
            name: "",
            email: "",
            password: "",
            repassword: "",
         },
      };
   },
   methods: {
      validate() {
         let isValid = true;

         this.errors = {
            name: "",
            email: "",
            password: "",
            repassword: "",
         };

         if (!this.user.name) {
            this.errors.name = "Họ và tên là bắt buộc";
            isValid = false;
         }
         if (!this.user.email) {
            this.errors.email = "Email là bắt buộc";
            isValid = false;
         }
         if (!this.user.password) {
            this.errors.password = "Mật khẩu là bắt buộc";
            isValid = false;
         }
         if (this.user.repassword != this.user.password) {
            this.errors.repassword = "Mật khẩu chưa đúng";
            isValid = false;
         }
         return isValid;
      },
      async register() {
         if (this.validate()) {
            try {
               await UserService.create(this.user);
               alert(
                  `Chúc mừng ${this.user.name.toUpperCase()} !!! Bạn đã đăng ký tài khoản thành công!`
               );
            } catch (error) {
               console.log(error);
            }
         }
      },
   },
};
</script>

<style scoped>
body{
    background-color: #080710;
}
.background{
    width: 430px;
    height: 520px;
    position: absolute;
    transform: translate(-50%,-50%);
    left: 50%;
    top: 50%;
}
.background .shape{
    height: 200px;
    width: 200px;
    position: absolute;
    border-radius: 50%;
}
.shape:first-child{
    background: linear-gradient(
        #1845ad,
        #23a2f6
    );
    left: -80px;
    top: -80px;
}
.shape:last-child{
    background: linear-gradient(
        to right,
        #ff512f,
        #f09819
    );
    right: -30px;
    bottom: -80px;
}
form{
    /* height: 700px; */
    width: 400px;
    background-color: rgba(255,255,255,0.13);
    position: absolute;
    transform: translate(-50%,-50%);
    top: 50%;
    left: 50%;
    border-radius: 10px;
    backdrop-filter: blur(10px);
    border: 2px solid rgba(255,255,255,0.1);
    box-shadow: 0 0 40px rgba(8,7,16,0.6);
    padding: 50px 35px;
}
form *{
    font-family: 'Poppins',sans-serif;
    color: #ffffff;
    letter-spacing: 0.5px;
    outline: none;
    border: none;
}
form h3{
    font-size: 32px;
    font-weight: 500;
    line-height: 42px;
    text-align: center;
}

label{
    display: block;
    margin-top: 30px;
    font-size: 16px;
    font-weight: 500;
}
input{
    display: block;
    height: 50px;
    width: 100%;
    background-color: rgba(255,255,255,0.07);
    border-radius: 3px;
    padding: 0 10px;
    margin-top: 8px;
    font-size: 14px;
    font-weight: 300;
}
::placeholder{
    color: #e5e5e5;
}
button{
    margin-top: 50px;
    width: 100%;
    background-color: #ffffff;
    color: #080710;
    padding: 15px 0;
    font-size: 18px;
    font-weight: 600;
    border-radius: 5px;
    cursor: pointer;
}
.social{
  margin-top: 30px;
  display: flex;
}
.social div{
  background: red;
  width: 150px;
  border-radius: 3px;
  padding: 5px 10px 10px 5px;
  background-color: rgba(255,255,255,0.27);
  color: #eaf0fb;
  text-align: center;
}
.social div:hover{
  background-color: rgba(255,255,255,0.47);
}
.social .fb{
  margin-left: 25px;
}
.social i{
  margin-right: 4px;
}
</style>
