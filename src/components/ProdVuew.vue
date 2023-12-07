<template>
  <div class="product-card">
    <img :src="pname.image" alt="Product Image" class="product-image">
    
    <div class="product-details">
      <h3>{{ pname.name }}</h3>
      <p class="product-description">{{ pname.description }}</p>
      <p class="product-price">price:$ {{ pname.price.toFixed(2) }}</p>
      <p class="product-availability" :class="{ 'available': pname.availability, 'not-available': !pname.availability }">
        {{ pname.availability ? 'Available' : 'Not Available' }}
      </p>
      
      <p class="product-care-tips">care Tips:{{ pname.careTips }}</p>
      <div v-if="pname.promotionalData" class="promotional-data">
       <div class="box">
        <p> Discount :  {{pname.promotionalData.discountPercentage }}%</p>
        <p> promo End Date :{{pname.promotionalData.promoEndDate }}</p>
</div>
      </div>
      <div class="product-revi">
        <h4>Review</h4>
      </div>
        <div class="product-reviews" v-if="pname.reviews.length === 0">No reviews yet.</div>
        <div v-else>
          <div v-for="review in pname.reviews" :key="review.user" class="review">
            <p><strong>{{ review.user }}</strong></p>
            <p>{{ '★'.repeat(review.rating) }}</p>
            <p>{{ review.comment }}</p>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
export default{
    name: 'ProdVuew',
    props:{
        pname: Array
    }
} 
</script>
<style>
.product-card {
  display: flex;
  border: 1px solid #ccc;
  border-radius: 8px;
  overflow: hidden;
  margin: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.product-image {
  padding: 20px;
  width: 200px;
height: 350px;

}

.product-details {
  padding: 15px;
  flex: 1;
  font-display: 20px;
}
.box {
  color: whitesmoke;
  display:inline-block;
  width: auto;
  height: auto;
  background-color: #ba1919;
  padding: 5px;
  border: 1px soild;
}

.product-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.product-price {
  font-weight: bold;
  color: #27ae60; /* Green color for price */
}

.product-description {
  margin-top: 10px;
  color: #555;
}

.availability-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
}

.product-availability {
  font-weight: bold;
}
.product-care-tips {
  color: #3498db; /* Blue color for care tips */
}
.review {
  border-bottom: 1px solid #ba1919;
}

.product-revi {
  color: red; /* Orange color for rating */
}

.comment {
  color: #777;
}
</style>
