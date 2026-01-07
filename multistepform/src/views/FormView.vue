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
                <button class="nextstep">Next step</button>
            </form>
        </div> -->
        <!-- <div class="content2">
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
                <input type="checkbox" id="switch" class="toggle-input"/><label class="toggle-label" for="switch">Toggle</label>
                <p>Early</p>
            </div>
            <button class="goback">Go back</button>
            <button class="nextstep">Next step</button>
        </div> -->
        <div class="content3">
            <h1>Pick add-ons</h1>
            <p class="content3-titlep">Add-ons help</p>
            <div>
                <div class="content3-select-item">
                    <input type="checkbox">
                    <div class="content3-text">
                        <h3>Online service</h3>
                        <p>Access to multiplayer games</p>
                    </div>
                    <p class="content3-price">+$1/mo</p>                    
                </div>
                <div class="content3-select-item">
                    <input type="checkbox">
                    <div class="content3-text">
                        <h3>Larger storage</h3>
                        <p>Extra 1TB of cloud save</p>
                    </div>
                    <p class="content3-price">+$2/mo</p>
                </div>
                <div class="content3-select-item">
                    <input type="checkbox">
                    <div class="content3-text">
                        <h3>Customizable profile</h3>
                        <p>Custom theme on your profile</p>
                    </div>
                    <p class="content3-price">+$2/mo</p>
                </div>
            </div>
            <button class="goback">Go back</button>
            <button class="nextstep">Next step</button>
        </div>
    </div>
  </div>
</template>

<style>
    
    .content3 h1{
        color: #2c4158;
        font-weight: 600;
        margin-bottom: 15px;
    }
    .content3-titlep {
        color: #888888;
        font-size: 16px;
        margin-bottom: 40px;
    }
    .content3-select-item {
        display: flex;
        margin-bottom: 30px;
        border: 1.5px solid #78409e;
        border-radius: 10px;
        padding: 20px 20px;
        align-items: center;
        justify-content: space-between;
        column-gap: 25px;
    }
    .content3-price {
        color: #78409e;
        font-weight: 500;
    }
    .content3-text {
        width: 100%;
    }
    .content3-text h3 {
        color: #2c4158;
    }
    .content3-text p {
        color: #888888;
        font-size: 16px;
    }
</style>
