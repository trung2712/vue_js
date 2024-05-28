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
  <label>Nhap FirstName</label>
  <input type="text" name="firstName" /> <br>
  <label>Nhap Email</label>
  <input type="text" name="Email" /> <br>
  <input type="submit" value="Đăng Nhập" />
</form>
<!--    v-bind:class cho phép bạn ràng buộc động các lớp CSS vào phần tử HTML -->
<!--    dựa trên dữ liệu của Vue instance,-->
<!--    giúp bạn dễ dàng kiểm soát và thay đổi giao diện người dùng dựa trên trạng thái hoặc -->
<!--    dữ liệu động trong ứng dụng của bạn.-->
    <button @click="changeActive"> Change Active</button>
    <div class="demo" v-bind:class="objClass"></div>
  </div>
</template>

<script>
import CompFooter from "./CompFooter.vue";

export default {
    name: 'comp-header',
  components: {CompFooter},
    data() {
        return {
            text: 'Header',
           click: 0,
          isActive : true,
          isError : false
        }
    },
  methods:{
    handlesubmit(e){
      console.log(e)
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
  computed : {
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


</style>
