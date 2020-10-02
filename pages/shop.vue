<template>
  <div>
    <h1>Shop</h1>
    <ul>
      <li v-for="(i,index) in 10" :key="index">
        สินค้า {{ i }} รูปภาพ ราคา สินค้า
        <nuxt-link :to="{ name: 'product-id', params: { id: i } }">
          ปุ่มรายละเอียด
        </nuxt-link>
        <!-- รูปภาพ
        ราคา ส่วนลด
        ปุ่มซื้อ
        ปุ่มรายละเอียด--->
      </li>
    </ul>
  </div>
</template>
<script>
export default {
}
</script>
<style>
</style>