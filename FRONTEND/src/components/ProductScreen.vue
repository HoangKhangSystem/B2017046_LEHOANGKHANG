<template>
   <div class="row">
      <div id="content" class="col-sm-12">
         <div class="header-content">
            <h3 class="title">Mô Hình</h3>
            <form class="form-inline my-2 my-lg-0 search-btn">
               <input
                  class="form-control mr-sm-2"
                  type="search"
                  placeholder="Tìm kiếm..."
                  aria-label="Search"
                  v-model="searchText"
               />
               <button
                  class="btn btn-outline-success my-2 my-sm-0"
                  type="submit"
               >
                  <i class="fas fa-search"></i>
               </button>
            </form>
         </div>
         <div class="row product-category">
            <div v-if="filteredProductsCount > 0"></div>
            <p class="non-product" v-else>Không có sản phẩm nào</p>
            <div
               class="product-grid col-lg-3"
               :key="index"
               v-for="(product, index) in filteredProducts"
            >
               <div class="thumb product-item">
                  <div class="image">
                     <a href="#"
                        ><img :src="product.imgUrl" alt="Sản phẩm"
                     /></a>
                  </div>
                  <div class="caption">
                     <h4>
                        <a href="#" class="product-name">
                           {{ product.name }}
                           
                           <!-- {{ product.description }} -->
                        </a>
                     </h4>
                     <p class="price">
                        {{
                           product.price.replace(/\B(?=(\d{3})+(?!\d))/g, ".")
                        }}
                        đồng
                     </p>
                  </div>
                  <div class="bottom-cart">
                     <button class="btn-cart" @click="addProductToCart(index)">
                        Thêm vào giỏ
                     </button>
                  </div>
               </div>
            </div>
         </div>
      </div>
   </div>
</template>

<script>
import ProductService from "../services/product.service";

export default {
   data() {
      return {
         products: [],
         searchText: "",
      };
   },

   computed: {
      productStrings() {
         return this.products.map((product) => {
            const { name, description } = product;
            return [name, description].join("");
         });
      },
      filteredProducts() {
         if (!this.searchText) return this.products;
         return this.products.filter((_product, index) =>
            this.productStrings[index].includes(this.searchText)
         );
      },
      filteredProductsCount() {
         return this.filteredProducts.length;
      },
   },
   methods: {
      async getAllProduct() {
         try {
            this.products = await ProductService.getAll();
         } catch (error) {
            console.log(error);
         }
      },
      async addProductToCart(index) {
         const saveLocalCart = JSON.parse(
            localStorage.getItem("localProductCart") ?? "[]"
         );
         for (const item of saveLocalCart) {
            if (item.id === this.products[index]._id) {
               item.amount++;
               const localProductCart = JSON.stringify(saveLocalCart);
               localStorage.setItem("localProductCart", localProductCart);
               alert(
                  `Số lượng sản phẩm ${this.products[index].name} đã được cập nhật`
               );
               return;
            }
         }
         const temp = {
            id: this.products[index]._id,
            name: this.products[index].name,
            imgUrl: this.products[index].imgUrl,
            price: this.products[index].price,
            description: this.products[index].description,
            amount: 1,
         };
         saveLocalCart.push(temp);
         const localProductCart = JSON.stringify(saveLocalCart);
         localStorage.setItem("localProductCart", localProductCart);
         alert(
            `Sản phẩm ${this.products[index].name} vừa được thêm vào giỏ hàng`
         );
      },
   },

   created() {
      this.getAllProduct();
   },
};
</script>

<style scoped>

.product-item {
   border: 1px solid #ddd;
   border-radius: 30px;
   overflow: hidden;
}

.product-grid:hover .product-item {
   border-color: red; /* Màu viền khi hover */
}
.row {
   padding-top: 30px;
}
#content {
   min-height: 400x;
}
.product-category {
   padding-top: 0px;
}
.header-content {
   display: flex;
   border-bottom: 3px solid #eee;
   font-weight: normal;
   font-size: 22px;
}
.search-btn {
   margin-left: 550px;
   padding-bottom: 5px;
}
.non-product {
   margin-left: 450px;
   margin-top: 15px;
   font-size: 20px;
   font-weight: bold;
   color: blue;
}
.product-grid {
   /* height: 300px; */
   position: relative;
   text-align: center;
   vertical-align: top;
   padding: 0px;
   margin-bottom: 15px;
   border: 3px solid transparent;
}
.product-grid:hover {
   border-color: greenyellow;
   border-radius: 30px;

}
.product-grid .thumb img {
   object-fit: cover;
   height: 150px;
}
.product-grid .thumb .caption h4 a {
   font-size: 13px;
   line-height: 22px;
   text-decoration: none;
   padding: 5px;
   color: #333;
   margin: 0 auto;
   width: 100%;
   overflow: hidden;
   text-overflow: ellipsis;
   -webkit-line-clamp: 2;
   display: -webkit-box;
   -webkit-box-orient: vertical;
}
.price {
   color: Black;
   font-weight: bold;
}
.btn-primary {
   background-color: #3e7cb4;
}
.botton-cart {
   position: absolute;
   bottom: 15px; /* Tăng khoảng cách từ bottom lên 15px */
   left: 50%;
   transform: translateX(-50%); /* Đưa phần tử về giữa theo chiều ngang */
}

.btn-cart {
   background-color: #ff4d4d; /* Đổi màu nền thành một đỏ tương tự nhưng có chút sáng hơn */
   color: #fff;
   border: none; /* Xóa đường viền */
   padding: 10px 20px; /* Tăng khoảng cách bên trong nút */
   font-size: 14px; /* Đặt kích thước chữ là 14px */
   cursor: pointer; /* Biến con trỏ thành bàn tay khi di chuột qua */
   transition: background-color 0.3s; /* Hiệu ứng màu nền thay đổi mượt mà */
   outline: none; /* Xóa đường viền khi nút được focus */
   border-radius: 5px; /* Giảm bán kính bo tròn để trông nhẹ nhàng hơn */
}

.btn-cart:hover {
   background-color: #4caf50; /* Đổi màu nền hover thành một xanh tươi mới */
}
</style>
<!-- <style scoped>

.product-item {
   border: 1px solid #ddd;
   border-radius: 8px;
   overflow: hidden;
}

.product-grid:hover .product-item {
   border-color: red; /* Màu viền khi hover */
}

.row {
   padding-top: 30px;
}

#content {
   min-height: 400x;
}

.product-category {
   padding-top: 0px;
}

.header-content {
   display: flex;
   border-bottom: 3px solid #eee;
   font-weight: normal;
   font-size: 22px;
}

.search-btn {
   margin-left: 550px;
   padding-bottom: 5px;
}

.non-product {
   margin-left: 450px;
   margin-top: 15px;
   font-size: 20px;
   font-weight: bold;
   color: blue;
}

.product-grid {
   height: 300px;
   position: relative;
   text-align: center;
   vertical-align: top;
   padding: 7px;
   margin-bottom: 15px;
   border: 3px solid transparent;
}

.product-grid:hover {
   border-color: #eae9e9;
}

.product-grid .thumb img {
   object-fit: cover;
   height: 150px;
}

.product-grid .thumb .caption h4 a {
   font-size: 13px;
   line-height: 22px;
   text-decoration: none;
   padding: 5px;
   color: #333;
   margin: 0 auto;
   width: 100%;
   overflow: hidden;
   text-overflow: ellipsis;
   -webkit-line-clamp: 2;
   display: -webkit-box;
   -webkit-box-orient: vertical;
}

.price {
   color: #ff0000;
   font-weight: bold;
}

.btn-primary {
   background-color: #3e7cb4;
}

.botton-cart {
   position: absolute;
   bottom: 0;
   left: calc(50% - 55px);
}

.btn-cart {
   background-color: #3e7cb4;
   color: #fff;
   border-radius: 3px;
   border: 1px solid #3e7cb4; /* Màu viền cho nút */
}

.btn-cart:hover {
   background-color: #1760a0;
   border: 1px solid #1760a0; /* Màu viền khi hover */
}
</style> -->

