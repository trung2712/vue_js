<template>
  <div>
    <h1>{{ text }}</h1>
    <div class="box" @click="handleclick">
      <p>click X : {{click}} </p>
<!--      .stop ngăn chặn truyền sự kiện lên thành phần cha-->
      <div class="box2" @click.stop="clickchild"></div>
    </div>
<!--    prevent ngăn chăn chuyển hướng sang đường link khác-->
<!--    Khi một biểu mẫu được gửi (thông qua nút submit hoặc sự kiện submit),-->
<!--    trình duyệt sẽ thu thập dữ liệu từ các trường nhập liệu trong biểu mẫu và -->
<!--    gửi chúng đến URL được chỉ định trong thuộc tính action của thẻ form-->
<form action="./server.php" v-on:submit.prevent="handlesubmit">
  <label>Nhap username</label>
  <input type="text" name="firstName" v-model="username"/> <br>
  <label>Nhap password</label>
  <input type="text" name="password" v-model="password" /> <br>
  <button type="submit">Đăng Nhập</button>
</form>


<!--    <form  v-on:submit.prevent="tinhTong">-->
    <form>

      {{nhapC}} <br>
<!--      <input type="number" name="A" v-model="a"/> <br>-->
      <label>Nhap B</label>
      <input type="number" name="B" v-model="b" /> <br>
<!--      <button type="submit">Tinh tong</button>-->
      <p>Tong moi</p>
      <input type="number" name="tongMoi" v-model="tongMoi" /> <br>

      <p>Tong cu</p>


    <input type="number" name="tong" v-model="tong" /> <br>

    <input type="number" name="hieu" v-model="hieu" /> <br>
    <input type="number" name="nhan" v-model="nhan" /> <br>
    <input type="number" name="chiaLayDu" v-model="chiaLayDu" /> <br>
    <input type="number" name="chiaLayPhanNguyen" v-model="chiaLayPhanNguyen" /> <br>
    </form>
<!--    v-bind:class cho phép bạn ràng buộc động các lớp CSS vào phần tử HTML -->
<!--    dựa trên dữ liệu của Vue instance,-->
<!--    giúp bạn dễ dàng kiểm soát và thay đổi giao diện người dùng dựa trên trạng thái hoặc -->
<!--    dữ liệu động trong ứng dụng của bạn.-->
    <button @click="changeActive"> Change Active</button>
    <div class="demo" v-bind:class="objClass"></div>
      <p :class="thongBao">{{message}}</p>
  </div>
</template>

<script>
import CompFooter from "./CompFooter.vue";

export default {
    name: 'comp-header',
  props : {
    nhapC : Number,

  },

  components: {CompFooter},
    data() {
        return {
            text: 'Header',
           click: 0,
          isActive : true,
          isError : false,
          status: "FAILED",
          color: "red",
          username: "",
          password: "",
          message: "",

          a: 0,
          b: 0,
          tongMoi: 0
        }
    },
  methods:{
    // tinhTong() {
      // this.tong = Number(this.a) + Number(this.b);
    // },
    handlesubmit(e){
      console.log(e)
      console.log(this.username);
      console.log(this.password);
      if (this.username === "abc" && this.password === "123") {
        this.color = "green";
        this.status = "SUCCESS";
        this.message = "Ban da dang nhap thanh cong"
      } else if (this.username !== "abc" && this.password !== "123") {
        this.color = "red";
        this.status = "FAILED";
        this.message = "Ban da sai ca tai khoan va mat khau, vui long kiem tra lai"
      } else {
        this.color = "yellow";
        this.status = "WARNING";
        this.message = "Ban da sai ca tai khoan hoac mat khau, vui long kiem tra lai"
      }
      console.log(this.color, this.status, this.message);
    },
    handleclick(e){
      console.log(e)
    },
    clickchild(e){
      console.log('clickchild',e.target)
    },
    // thay đổi giá trị tiếp ngược lại với giá trí trước
    changeActive(){
      this.isActive = !this.isActive
    }
  },
  watch: {
      // Theo doi su thay doi của các thuộc tính của component trong function và thực hiện 1 hành động nào đó
    // Theo doi a, neu a thay đổi thì thực thi function bên phải
    nhapC: function () {
      this.tongMoi = Number(this.nhapC) + Number(this.b);
      console.log(this.nhapC)
      console.log("a thay doi , Tong moi = ", this.tongMoi)
    },
    a: function () {
      this.tongMoi = Number(this.nhapC) + Number(this.b);
      console.log("a thay doi , Tong moi = ", this.tongMoi)
    },
    b: function () {
      this.tongMoi = Number(this.nhapC) + Number(this.b);
      console.log(this.nhapC)
      console.log("b thay doi , Tong moi = ", this.tongMoi)
    }
    // tong: function () {
    //   this.tongMoi = this.tong + 1;
    //   console.log("Tong thay doi , Tong moi = ", this.tongMoi)
    // }
  },
  computed : {
      // Tao ra 1  thuộc tính moi , có gia tri bang ket  qua trả về của function định nghĩa cho thuộc tính đó
      tong: function () {
        return Number(this.a) + Number(this.b);
      },
     hieu: function () {
      return Number(this.a) - Number(this.b);
    },
    nhan: function () {
      return Number(this.a) * Number(this.b);
    },
    chiaLayDu: function () {
      return Number(this.a) % Number(this.b);
    },
    chiaLayPhanNguyen: function () {
      return Number(this.a) / Number(this.b);
    },
      thongBao: function () {
        return {
          nenCam: this.status === "FAILED",
          red: this.status === "FAILED",
          green: this.status === "SUCCESS",
          nenXanh: this.status === "SUCCESS",
          yellow: this.status === "WARNING",
          gray: this.status === "WARNING",
        }
      },
      objClass : function () {
        return{
          active:this.isActive,
          error :this.isError
        }
      }

  }
}
</script>

<style>
.box{
  width: 300px;
  height: 200px;
  background-color: royalblue;
  margin: 200px;
}
.box2{
  width:50px;
  height:50px;
  background-color: rebeccapurple;
}
.demo{
  width: 50px;
  height: 50px;
  background-color: yellowgreen;
}
.demo.error{
  background-color: red;
}
.demo.active{
  background-color: orange;
}

.red {
  color: red;
}


.green {
  color: green;
}

.yellow {
  color: yellow;
}

.nenCam {
  background-color: orange;
}

.nenXanh {
  background-color: #2c3e50;
}

.gray {
  background-color: grey;
}
</style>
