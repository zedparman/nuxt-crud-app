<template>
  <b-col md="4" class="m-3">
      <b-card header="Add Product">
        <b-card-body>
            <b-form autocomplete="off">
                <b-form-group  
                label="Name"
                >
                    <b-form-input v-model="form.name" id="name" name="name"  trim></b-form-input>
                </b-form-group>
                <b-form-group  
                label="Price ($)"
                >
                    <b-form-input v-model="form.price" id="price" name="price"  trim></b-form-input>
                </b-form-group>
                <b-form-group  
                label="Brand"
                >
                    <b-form-input v-model="form.brand" id="brand" name="brand"  trim></b-form-input>
                </b-form-group>
                <b-form-group label="Inventory">
                    <b-form-radio  v-model="form.inventoryStatus" name="inventorystatus" value="true">In Stock</b-form-radio>
                    <b-form-radio  v-model="form.inventoryStatus" name="inventorystatus" value="false">Out of Stock</b-form-radio>
                </b-form-group>
            </b-form>
        </b-card-body>
        <b-button block  variant="primary" @click="addProduct">Add a Product</b-button>
  </b-card>
  </b-col>
</template>

<script>
export default {
    data() {
        return {
            form: {
                name:'',
                price: '',
                Brand: '',
                InventoryStatus: ''

            }
        }
    },
    methods: {
        addProduct() {
            console.log(this.form);
            this.$emit('addProduct', {
                name: this.form.name,
                price: '$' + this.form.price,
                brand: this.form.brand,
                inventoryStatus: this.form.inventoryStatus === 'true'

            })
        }
    }
}
</script>

<style>

</style>