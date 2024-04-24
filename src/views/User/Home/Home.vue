<template>
  <div class="containPage">
    <div>
      <div class="titlePage d-flex justify-content-center">
        <h2 class="gradient-text">NAVYBOOKS</h2>
      </div>
      <div class="d-flex justify-content-end">
        <router-link to="/about" class="text-decoration-none">
          <button class="btnReadMore">Mượn ngay</button>
        </router-link>
      </div>
      <div class="contentPage d-flex flex-column">

        <div class="row">
          <div class="img-container1 img-container mt-5 ms-2">
            <img src="../../../assets/imgbanner/book2.avif" alt="Img1">
          </div>
          <div class="img-container2 img-container d-flex flex-column justify-content-center align-items-center">
            <h2>Chào mừng đến với NAVYBOOKS </h2>
            <text>Nơi mà bạn có thể khám phá ra nhiều chân trời mới qua sách.
                Những quyển sách hay và sâu sắc đang chờ đón bạn đến để mở rộng vốn tri thức của mình.
            </text>
          </div>
        </div>

        <div class="row">
          <div class="img-container3 img-container mt-5 mb-2 ms-2">
            <img src="../../../assets/imgbanner/book4.jpeg" alt="Img3">
          </div>
          <div class="img-container4 img-container ">
            <img src="../../../assets/imgbanner/book1.avif" alt="Img4">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
</script>

<style lang="scss" scoped>
@import "./Home.scss";

.img-container {
  flex: 1; /* Tự mở rộng để điều chỉnh kích thước */
  margin-right: 20px; /* Khoảng cách giữa các hình ảnh */
}

.single {
  flex-basis: 100%; /* Hình ảnh hàng đầu tiên có chiều rộng 100% */
}

.row {
  display: flex; /* Sắp xếp các hình ảnh trong một hàng */
  margin-bottom: 20px; /* Khoảng cách giữa các hàng */
}

.row:last-child {
  margin-bottom: 0; /* Không có khoảng cách dưới hàng cuối cùng */
}
</style>
