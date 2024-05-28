<template>
    <div>
      <h1>{{ textFooter }}</h1>
      <h2>Count :{{count}}</h2>
      <button v-on:click="bamVao(5)">click me</button>
      <button @click="a++">A=A+1</button>
      <button @click="b++">B=B+1</button>
      <p> Number + A = {{addA }}</p>
      <p> Number + B = {{addB }}</p>
<!--      v-model là một directive mạnh mẽ trong Vue.js, -->
<!--      được sử dụng để tạo liên kết hai chiều giữa dữ liệu trong Vue component -->
<!--      và các phần tử đầu vào của biểu mẫu-->
      <div>
        <h1> firstName = {{ firstname }}</h1>
        <input v-model="firstname" type="text" placeholder=" nhập firstName" /> <br>
      </div>
    </div>
</template>

<script>
export default {
    name: 'comp-footer',
  data() {
        return {
            textFooter: 'Hello Footer',
            count : 0,
          a : 0,
          b : 0,
          number : 20,
          firstname : ''
        }
  },
  methods :{
      bamVao (number) {
        // console.log('click' , this);
        this.count += number;
      },
  },
  // Methods: Mỗi lần component được render lại, method sẽ được gọi lại và tính toán lại kết quả.
  // Computed Properties: Chỉ tính toán lại khi các thuộc tính phụ thuộc thay đổi,
  // giúp tối ưu hiệu suất.
  computed :{
    addA(){
      console.log( 'runa');
      return this.a + this.number;
    },
    addB(){
      console.log('runb');
      return this.b + this.number;
    }
  },

  // mounted() {
  //   confirm('Xác nhận bạn đã đủ tuổi');
  //   prompt('điền số tuổi vào')
  //   setInterval(function () {
  //     // console.log('thông báo')
  //   }, 1000)
  // }
}
</script>

<style>

</style>
