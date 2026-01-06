<script setup>
// IMAGES IMAGES IMAGES IMAGES IMAGES
// import leftBgImage from "@/assets/images/bg-sidebar-desktop.svg";
const leftBgImage = '/images/bg-sidebar-desktop.svg';
// IMAGES IMAGES IMAGES IMAGES IMAGES
</script>

<template>
  <div class="container">
    <div class="left-nav" :style="{ backgroundImage: `url(${leftBgImage})` }">
        <div class="nav">
            <div class="nav-item">
                <button>1</button>
                <div class="nav-item-text">
                    <h4>STEP 1</h4>
                    <p>YOUR INFO</p>
                </div>
            </div>
            <div class="nav-item">
                <button>2</button>
                <div class="nav-item-text">
                    <h4>STEP 2</h4>
                    <p>SELECT PLAN</p>
                </div>
            </div>
            <div class="nav-item">
                <button>3</button>
                <div class="nav-item-text">
                    <h4>STEP 3</h4>
                    <p>ADD-ONS</p>
                </div>
            </div>
            <div class="nav-item">
                <button>4</button>
                <div class="nav-item-text">
                    <h4>STEP 4</h4>
                    <p>SUMMARY</p>
                </div>
            </div>
        </div>
    </div>
    <div class="right-form">

    </div>
  </div>
</template>

<style>
    .left-nav {
  width: 274px; /* По макету из Frontend Mentor */
  height: 568px; /* По макету */
  background-size: cover; /* Чтобы SVG заполнило весь блок */
  background-position: center;
  background-repeat: no-repeat;
  border: 2px solid red; /* Временная граница для отладки */
}

</style>
