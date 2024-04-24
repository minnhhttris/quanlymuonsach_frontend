<template>
  <div class="containPage">
    <div class="titlePage">
    </div>
    <div class="contentPage">
      <section class="h-100 gradient-custom-2">
        <div class="h-100">
          <div class="row d-flex justify-content-center align-items-center h-100">
            <div class="col">
              <div class="card" style="background-color: #8fabd083">
                <div class="rounded-top text-white d-flex flex-row bgProfile">
                  <div class="mt-5 d-flex flex-column justify-content-center">
                    <div class="image-avatar d-flex justify-content-center" >
                      <img v-if="data.Avatar != undefined" :src="'http://localhost:3000/' + data.Avatar"
                        alt="Generic placeholder image" class="img-fluid img-thumbnail mt-4 mb-2"
                        />
                    </div>
                    <div class="d-flex justify-content-center">
                      <router-link to="/editprofile" style="z-index: 1" class="btn btn-edit">
                      <button type="button" data-mdb-ripple-color="dark">
                        Chỉnh sửa
                      </button>
                    </router-link>
                    </div>
                    
                  </div>
                  <div class="" style="margin-top: 130px; margin-left: 20px">
                    <h5>{{ data.Ten }}</h5>
                    <p>{{ data.DiaChi }}</p>
                  </div>
                </div>

                <div class="card-body text-black">
                  <div class="mb-5">
                    <p class="lead fw-normal mb-1 d-flex justify-content-center">Thông tin cá nhân độc giả</p>
                    <div class="">
                      <div class="card-body">
                        <div class="row">
                          <div class="col-sm-3">
                            <p class="mb-0">Họ tên</p>
                          </div>
                          <div class="col-sm-9">
                            <p class="text-muted mb-0">{{ data.Ten }}</p>
                          </div>
                        </div>
                        <hr />
                        <div class="row">
                          <div class="col-sm-3">
                            <p class="mb-0">Số điện thoại</p>
                          </div>
                          <div class="col-sm-9">
                            <p class="text-muted mb-0">
                              {{ data.DienThoai }}
                            </p>
                          </div>
                        </div>
                        <hr />
                        <div class="row">
                          <div class="col-sm-3">
                            <p class="mb-0">Địa chỉ</p>
                          </div>
                          <div class="col-sm-9">
                            <p class="text-muted mb-0">{{ data.DiaChi }}</p>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import axios from "axios";
import { ref } from "vue";
const data = ref({});
const ID_DG = localStorage.getItem("ID_DG");
const fetchData = () => {
  axios
    .get("http://localhost:3000/authentication/info/" + ID_DG)
    .then((res) => {
      data.value = res.data;
      console.log(data.value);
    })
    .catch((err) => console.log(err));
};
fetchData();
</script>
<style lang="scss" scoped>
@import "./Profile.scss";
</style>