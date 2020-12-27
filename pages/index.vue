<template>
  <div>
    <AppHeader />
    <b-container>
      <b-row class="justify-content-center">
        <AddProduct @addProduct="addProduct"/>
        <ListProduct :products="productList"/>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import AppHeader from '../components/AppHeader'
import AddProduct from '../components/AddProduct'
import ListProduct from '../components/ListProduct'
import axios from 'axios'
export default {
  name:'app',
  components: {
    AppHeader,
    AddProduct,
    ListProduct
  },
  data() {
    return {
      productList: []
    }
  },
  methods: {
    async getProductList() {
      try{
        let result = await axios.get('http://localhost:4000/products')
        console.log('result', result.data)
        this.productList = result.data;
      }catch (error){
        console.log('Error', error)
      }
    },
    async AddProduct(newProduct) {
      console.log('newProduct', newProduct)
      try{
        await axios.post('http://localhost:4000/products', newProduct);
        this.getProductList();
        console.log('newProduct', newProduct)
      }catch(error){
        console.log('Error', error)
      }
    }
  },
  mounted() {
    this.getProductList();
  }
}
</script>

<style>

</style>