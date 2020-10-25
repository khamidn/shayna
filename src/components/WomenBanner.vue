<template>
	<!-- Women Banner Section Begin -->
    <section class="women-banner spad">
        <div class="container-fluid">
            <div class="row">
                <div class="col-lg-12 mt-5" v-if="products.length > 0">
                    <carousel class="product-slider" :items="3" :nav="false" :dots="false" :autoPlay="false">

                        <div class="product-item" v-for="item in products" :key="item.id">
                            <div class="pi-pic">
                                <img :src="item.galleries[0].photo" alt="" />
                                <ul>
                                    <li class="w-icon active">
                                        <a  @click="saveKeranjang(item.id, item.name, item.price, item.galleries[0].photo)" href="#"><i class="icon_bag_alt"></i></a>
                                    </li>
                                    
                                    <li class="quick-view"><router-link :to="'/product/'+item.id">+ Quick View </router-link></li>
                                   
                                </ul>
                            </div>
                            <div class="pi-text">
                                <div class="catagory-name">{{ item.type }}</div>
                                <router-link to="/product">
                                <a href="#">
                                    <h5>{{ item.name }}</h5>
                                </a>
                                </router-link>
                                <div class="product-price">
                                    ${{ item.price }}
                                    <span>$35.00</span>
                                </div>
                            </div>
                        </div>
                        
                    </carousel>
                </div>
                <div class="col-lg-12" v-else>
                    <p>
                        Produk tidak ditemukan
                    </p>
                </div>
            </div>
        </div>
    </section>
    <!-- Women Banner Section End -->
</template>

<script>
	import carousel from 'vue-owl-carousel';
    import axios from 'axios';


	export default {
		name: 'WomenBanner',
		components: {
			carousel
		},
        data() {
            return {
                products: [],
                keranjangUser:[]

            }
        },

        methods: {
            saveKeranjang(idProduct, nameProduct, priceProduct, photoProduct) {
                var productStore = {
                  "id" : idProduct,
                  "name" : nameProduct,
                  "price" : priceProduct,
                  "photo" : photoProduct
                }

                this.keranjangUser.push(productStore);
                const parsed = JSON.stringify(this.keranjangUser);
                localStorage.setItem('keranjangUser', parsed);
          }
        },

        mounted() {

            if (localStorage.getItem('keranjangUser')) {
              try {
                this.keranjangUser = JSON.parse(localStorage.getItem('keranjangUser'));
              } catch(e) {
                localStorage.removeItem('localStorage')
              }
            }

            axios
                .get("http://localhost:8000/api/products")
                .then(res => (this.products = res.data.data.data))
                .catch(err => console.log(err))
        }
	}
</script>

<style scoped="">
	.product-item {
		margin-right: 25px;
	}
</style>