<template>
  <div class="wrapper">
    <div class="header">
      <div class="nav-menu">
        <NavMenu />
      </div>
    </div>
    <div class="container">
      <div class="contact-info">
        <p>
          <i class="fa-solid fa-location-dot"></i>
          <a href="https://ctu.edu.vn">
            Trường Đại Học Cần Thơ Khu II, Đ. 3/2, Xuân Khánh, Ninh Kiều, Cần
            Thơ
          </a>
        </p>
        <p>
          <i class="fa-solid fa-school"></i>
          Khoa công nghệ thông tin và truyền thông
        </p>
        <p>
          <i class="fa-solid fa-envelope icon-email"></i>
          <a href="mailto:khang@gmail.com" class="contact-link">khang@gmail.com</a>
        </p>
        <p>
          <i class="fa-solid fa-phone icon-phone"></i>
          +84 0834667340
        </p>
      </div>

      <div class="feedback-form">
        <div class="form-group row">
          <label class="col-sm-2 col-form-label">Đóng góp ý kiến</label>
          <div class="col-sm-8">
            <textarea class="form-control" rows="7"></textarea>
            <div class="button-group">
              <button type="submit" class="btn btn-primary" @click="feedback">
                Gửi
              </button>
              <button type="reset" class="btn btn-danger ml-2">
                Xóa
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavMenu from "../components/NavMenu.vue";

export default {
  components: {
    NavMenu,
  },
  methods: {
    feedback() {
      alert("Cảm ơn bạn đã đóng góp ý kiến!!");
    },
  },
};
</script>

<style scoped>
.wrapper {
  max-width: 100%;
  background-color: #fff;
  font-family: "Open Sans", sans-serif;
  padding-bottom: 50px;
}

.header {
  width: 100%;
  height: auto;
}

.container {
  text-align: center;
  margin-top: 10px;
  color: #333;
}

.contact-info p {
  margin-bottom: 10px;
}

.contact-info i {
  margin-right: 5px;
  color: #1fcc44;
}

.contact-link {
  color: #1fcc44;
}

.feedback-form {
  margin-top: 20px;
}

.form-group {
  margin-bottom: 20px;
}

.button-group {
  margin-top: 10px;
}

.btn-primary {
  background-color: #1fcc44;
  color: #fff;
}

.btn-danger {
  background-color: #ff3f70;
  color: #fff;
}
</style>
