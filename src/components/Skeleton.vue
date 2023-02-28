<template>
    <div class="container-skeleton">
        <div class="bg-skeleton"></div>
        <div class="card-skeleton">
          <div class="areaimg-skeleton">
            <div class="img-skeleton"></div>
          </div>
          <div class="areacontent-skeleton">
            <div class="title-skeleton"></div>
            <div class="arearating-skeleton">
              <div class="category-skeleton"></div>
              <div class="rating-skeleton"></div>
            </div>
            <div class="desk-skeleton"></div>
            <div>
              <div class="price-skeleton"></div>
              <div class="areabtn-skeleton">
                <div class="btn-skeleton"></div>
                <div class="btn-skeleton"></div>
              </div>
            </div>
          </div>
        </div>
    </div>
</template>

<script>

</script>

<style scoped>
.container-skeleton {
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: var(--background-default);
}

.bg-skeleton{
  height: 70%;
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 10;
  background-color: var(--primary);
  animation: pulse 2s infinite ease-in-out;
} 

.card-skeleton{
  border-radius: 10px;
  z-index: 20;
  width: 80%;
  height: 70%;
  background-color: var(--secondary);
  display: flex;
  padding: 20px 40px;
}

.areaimg-skeleton{
  display: flex;
  width: 220px;
  justify-content: center;
  align-items: center;
  padding: 0 80px;
  background-color: var(--primary);
  animation: pulse 2s infinite ease-in-out;
}

.areacontent-skeleton{
  padding: 0 20px;
  width: 100%;
  height: 100%;
}

.title-skeleton{
  height: 40px;
  width: 100%;
  background-color: var(--primary);
  animation: pulse 2s infinite ease-in-out;
}

.arearating-skeleton{
  width: 100%;
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}

.category-skeleton{
  height: 40px;
  width: 40%;
  background-color: var(--primary);
  animation: pulse 2s infinite ease-in-out;
}

.rating-skeleton{
  height: 40px;
  width: 50%;
  background-color: var(--primary);
  animation: pulse 2s infinite ease-in-out;
}

.desk-skeleton{
  height: 160px;
  background-color: var(--primary);
  animation: pulse 2s infinite ease-in-out;
  margin: 40px 0;
}

.price-skeleton{
  width: 40%;
  height: 20px;
  background-color: var(--primary);
  animation: pulse 2s infinite ease-in-out;
  margin-bottom: 20px;
}

.areabtn-skeleton{
  display: flex;
  justify-content: space-between;
}

.btn-skeleton{
  width: 45%;
  height: 80px;
  background-color: var(--primary);
  animation: pulse 2s infinite ease-in-out;
}

@media (max-width: 767px) {
  .card-skeleton{
    flex-direction: column;
    height: auto;
  }

  .areaimg-skeleton{
    display: flex;
    width: 100%;
  }
  
  .btn-skeleton{
  width: 45%;
  height: 40px;
}
}
</style>