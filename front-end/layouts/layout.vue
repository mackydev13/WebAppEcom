<script>
import Navigation from "../components/Navigation.vue";
import couracel from "../components/couracel.vue";
import category from "../components/category.vue";
import featuredProduct from "../components/featured-product.vue";
import footer from '../components/footer.vue';
</script>
<template>
    <v-nav>
        <navigation />
    </v-nav>
    <couracel />
    <div>
        <category/>
    </div>
    <div>
        <featured-product/>
    </div>
    <footer />
</template>