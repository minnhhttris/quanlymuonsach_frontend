<template>
    <div class="containPage" v-if="isLogin">
      
    <div class="d-flex">
      <h2>Nhà Xuất Bản</h2>
      <div class="ml-auto">
        <button v-if="isLogin" @click="showModal1" class="btnAdd" style="margin-right: 10px;">
          <i class="fa-solid fa-industry"></i> Thêm NXB
      </button>
      </div>
      
    </div>
      <div class="contentPage" :style="`${isLogin ? '' : 'display: none'}`">
        <a-tabs v-model:activeKey="activeKey">
          <a-tab-pane key="1" tab="Nhà Xuất Bản">
            <h4>Danh sách Nhà Xuất Bản</h4>
            <a-table :dataSource="data" :columns="columns" rowKey="_id">
              <template  #action="{ record }" >
                <span class="action_group">
                  <a class="text-warning" @click="handleEdit(record)">Chỉnh sửa</a>
                  <a class="text-danger" @click="handleDelete(record)">Xóa</a>
                </span>
              
            </template>
             
            </a-table>
          </a-tab-pane>
        </a-tabs>
      </div>
    </div>
    <div v-else class="denied">
      <h3 class="text-center mt-5">Vui lòng đăng nhập để sử dụng dịch vụ</h3>
    </div>
  
  
    <!-- Modal Edit NXB -->
    <a-modal
          style="top: 40px"
          v-model:open="isModal1"
          width="800px"
          title="Chỉnh sửa NXB"
          @ok="handleOk"
          @cancel=""
          okText="Chỉnh sửa NXB"
          cancelText="Đóng"
        >
          <form action="" enctype="multipart/form-data">
            <div class="contentModal row">
              <div class="rightModal col">
                <div class="groupForm">
                  <span>Tên NXB:</span>
                  <input
                    type="text"
                    class="inputGroup"
                    v-model="tenNxb"
                    name="tenNxb"
                    id=""
                    autocomplete="off"
                  />
                </div>
                <p class="errorText text-danger" v-if="errors.TenNxb">{{ errors.TenNxb }}</p>
  
                <div class="groupForm">
                  <span>Địa chỉ:</span>
                  <input
                    type="text"
                    class="inputGroup "
                    v-model="diaChi"
                    name="diaChi"
                    id="diaChi"
                    autocomplete="off"
                  />
                </div>
                <p class="errorText text-danger" v-if="errors.DiaChi">{{ errors.DiaChi }}</p>
  
              </div>
            </div>
          </form>
        </a-modal>
  </template>
  
  <script setup>
  import { toast } from "vue3-toastify";
  import { ref } from "vue";
  import axios from "axios";
  
  const activeKey = ref("1");
  const data = ref([]);
  const isLogin = localStorage.getItem("isLogin");
  const columns = [
    {
      title: "Id Nhà xuất bản",
      dataIndex: "_id",
      key: "_id",
    },
    {
      title: "Tên Nhà Xuất Bản",
      dataIndex: "TenNxb",
      key: "TenNxb",
    },
    {
      title: "Địa chỉ",
      dataIndex: "DiaChi",
      key: "DiaChi",
    },
    {
      title: 'Thao tác',
      key: 'action',
      slots: {
        customRender: 'action',
      },
    },
  ];
  
  const isModal1 = ref(false);
  
  const errors = ref({
    TenNxb: "",
    DiaChi: "",});

const showModal1 = () => {
  isModal1.value = true;
};

const fetchData = () => {
  axios
    .get("http://localhost:3000/published")
    .then((res) => {
      data.value = res.data;
    })
    .catch((err) => console.log(err));
};

fetchData();

const handleValidate = () => {
  errors.value.TenNxb = tenNxb.value.trim() ? "" : "Vui lòng nhập tên NXB";
  errors.value.DiaChi = diaChi.value.trim() ? "" : "Vui lòng nhập Địa chỉ";
};

const handleOk = () =>{
  handleValidate();
  const TenNxb = tenNxb.value;
  const DiaChi = diaChi.value;
  const formData = {TenNxb,DiaChi};
  console.log(formData);
  const isValid = Object.values(errors.value).every((error) => !error);
  if (isValid) {
    const idUpdate = idEdit.value;
    console.log(idUpdate);
    console.log(`http://localhost:3000/published/${idUpdate}`);
    axios
      .put("http://localhost:3000/published/"+ idUpdate,{TenNxb,DiaChi} )
      .then((res) => {
        if (res.data.error) {
          toast.error(res.data.error);
        } else if (res.data.update) {
          toast.info(res.data.update);
          fetchData();
        } else {
          toast.success(res.data.message);
          fetchData();
        }
      })
      .catch((err) => console.log(err));
  } else {
    console.log("Form is invalid. Please check your inputs.");
  }
}
const tenNxb = ref("");
const diaChi = ref("");
const idEdit = ref("");
const handleEdit = (record) => {
  tenNxb.value = record.TenNxb;
  diaChi.value = record.DiaChi;
  idEdit.value = record._id;
  console.log(idEdit.value);
  showModal1();
};
const handleDelete = (record) => {
  // Xử lý xóa
};
</script>

<style lang="scss" scoped>
@import "./PublisherAdmin.scss";
</style>