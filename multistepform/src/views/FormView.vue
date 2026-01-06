<script setup>
    import { ref } from "vue";
// IMAGES IMAGES IMAGES IMAGES IMAGES
// import leftBgImage from "@/assets/images/bg-sidebar-desktop.svg";
const leftBgImage = '/images/bg-sidebar-desktop.svg';
// IMAGES IMAGES IMAGES IMAGES IMAGES

const currentStep = ref(1);
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

        <!-- <div class="content1">
            <h1>Personal info</h1>
            <p>Please provide your name, email address, and phone number.</p>
            <form class="form">
                <label for="name">Name</label>
                <input type="text" placeholder="name" id="name">
                <label for="email">Email address</label>
                <input type="text" placeholder="email" id="email">
                <label for="phone">Phone Number</label>
                <input type="text" placeholder="+79921229322" id="phone">
                <button>Next step</button>
            </form>
        </div> -->
        <div class="content2">
            <h1>Select your plan</h1>
            <p class="content2-titlep">You have the option of monthly or yearly billing</p>
            <div class="select-div">
                <div class="select-item">
                    <img src="/images/icon-arcade.svg" alt="img" class="select-img"> 
                    <h3>Arcade</h3>
                    <p>$9/mo</p>
                </div>
                <div class="select-item">
                    <img src="/images/icon-advanced.svg" alt="img" class="select-img">
                    <h3>Advanced</h3>
                    <p>$12/mo</p>
                </div>
                <div class="select-item">
                    <img src="/images/icon-pro.svg" alt="img" class="select-img">
                    <h3>Pro</h3>
                    <p>$15/mo</p>
                </div>
            </div>
            <div class="check">
                <p>Monthly</p>
                <p>Early</p>
            </div>
            <button>Go back</button>
            <button>Next step</button>
        </div>
    </div>
  </div>
</template>

<style>
    .content2 h1{
        color: #2c4158;
        font-weight: 600;
        margin-bottom: 15px;
    }
    .content2-titlep {
        color: #888888;
        font-size: 16px;
        margin-bottom: 40px;
    }
    .select-div {
        display: flex;
        flex-direction: row;
        column-gap: 20px;
        justify-content: space-around;
        margin-bottom: 30px;

    }
    .select-item {  
        border: 1px solid #000;
        border-radius: 10px;
        width: 100%;
        padding: 20px 20px 20px 20px;
    }
    .select-item h3 {
        margin-bottom: 6px;
    }
    .check {
        display: flex;
        flex-direction: row;
        width: 100%;
        background-color: #eefaff;
        padding-top: 20px;
        padding-bottom: 20px;
        align-items: center;
        justify-content: center;
    }
    .check p {
        font-weight: 600;
    }
    .select-img {
        margin-bottom: 40px;
    }
</style>
