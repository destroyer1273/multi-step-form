<script setup>
    import { ref, computed } from "vue";
// IMAGES IMAGES IMAGES IMAGES IMAGES
// import leftBgImage from "@/assets/images/bg-sidebar-desktop.svg";
const leftBgImage = '/images/bg-sidebar-desktop.svg';
// IMAGES IMAGES IMAGES IMAGES IMAGES

const currentStep = ref(1);
const personalData = ref({});
const plans = {
    monthly: [
        {name: "Arcade (Monthly)", price: "$9/mo", cost: 9},
        {name: "Advanced (Monthly)", price: "$12/mo", cost: 12},
        {name: "Pro (Monthly)", price: "$15/mo", cost: 15}
    ],
    yearly: [
        {name: "Arcade (Yearly)", price: "$90/yr", cost: 90},
        {name: "Advanced (Yearly)", price: "$120/yr", cost: 120},
        {name: "Pro (Yearly)", price: "$150/yr", cost: 150}
    ]
};
const addOns = {
    monthly: [
        {name: "Online service", price: "+$1/mo", key: "onlineService", cost: 1},
        {name: "Larger storage", price: "+$2/mo", key: "largerStorage", cost: 2},
        {name: "Customizable profile", price: "+$2/mo", key: "customizableProfile", cost: 2}
    ], 
    yearly: [
        {name: "Online service", price: "+$10/yr", key: "onlineService", cost: 10},
        {name: "Larger storage", price: "+$20/yr", key: "largerStorage", cost: 20},
        {name: "Customizable profile", price: "+$20/yr", key: "customizableProfile", cost: 20}
    ]
};
const finalData = computed(() => {
    let obj = {};
    obj.totalCount = 0;
    if(!personalData.value.monthly) {
        obj.plan = plans.monthly[personalData.value.selectedPlan-1];
        obj.addOns = addOns.monthly.filter(function(item) {
            if(personalData.value.addOns[item.key] == true) {
                return true;
            }
        });
    } else {
        obj.plan = plans.yearly[personalData.value.selectedPlan-1];
        obj.addOns = addOns.yearly.filter(function(item) {
            if(personalData.value.addOns[item.key] == true) {
                return true;
            }
        });
    }
    obj.totalCount += obj.plan.cost;
    if(obj.addOns) {
        for(const item of obj.addOns) {
            obj.totalCount += item.cost;
        }
    }
    return obj;
});
// const selectedItem = ref(1);
personalData.value.selectedPlan = 1;
personalData.value.monthly = false;
personalData.value.addOns = {
    "onlineService": false,
    "largerStorage": false,
    "customizableProfile": false,
};
personalData.value.name = "";
personalData.value.email = "";
personalData.value.phone = "";
const allFields = ref(false);
const selectOther = (numOfSelected) => {
    personalData.value.selectedPlan = numOfSelected; 
};

const goForward = () => {
    if(currentStep.value < 4 && currentStep.value > 0) {
        if(currentStep.value == 1 && (personalData.value.name == "" || personalData.value.phone == "" || personalData.value.email == "")) {
            allFields.value = true;
        } else {
            allFields.value = false;
            currentStep.value = currentStep.value + 1;
        }
    }
    console.log("Plan", finalData.value.plan, "AddOns", finalData.value.addOns, "TotalCount", finalData.value.totalCount);
};
const goBack = () => {
    if(currentStep != 1) {
        currentStep.value = currentStep.value - 1;
    }
};
const confirm = () => {
    currentStep.value = 5;
};
</script>

<template>
  <div class="container">
    <div class="left-nav" :style="{ backgroundImage: `url(${leftBgImage})` }">
        <div class="nav">
            <div class="nav-item">
                <button :style="{backgroundColor: currentStep==1 ? '#FFF' : 'inherit', color: currentStep == 1 ? 'black' : '#FFF'}">1</button>
                <div class="nav-item-text">
                    <h4>STEP 1</h4>
                    <p>YOUR INFO</p>
                </div>
            </div>
            <div class="nav-item">
                <button :style="{backgroundColor: currentStep==2 ? '#FFF' : 'inherit', color: currentStep == 2 ? 'black' : '#FFF'}">2</button>
                <div class="nav-item-text">
                    <h4>STEP 2</h4>
                    <p>SELECT PLAN</p>
                </div>
            </div>
            <div class="nav-item">
                <button :style="{backgroundColor: currentStep==3 ? '#FFF' : 'inherit', color: currentStep == 3 ? 'black' : '#FFF'}">3</button>
                <div class="nav-item-text">
                    <h4>STEP 3</h4>
                    <p>ADD-ONS</p>
                </div>
            </div>
            <div class="nav-item">
                <button :style="{backgroundColor: currentStep==4 || currentStep==5 ? '#FFF' : 'inherit', color: currentStep == 4 || currentStep==5 ? 'black' : '#FFF'}">4</button>
                <div class="nav-item-text">
                    <h4>STEP 4</h4>
                    <p>SUMMARY</p>
                </div>
            </div>
        </div>
    </div>
    <div class="right-form">

        <div v-if="currentStep === 1" class="content1">
            <h1>Personal info</h1>
            <p class="content1-titlep">Please provide your name, email address, and phone number.</p>
            <form class="form">
                <label for="name">Name</label>
                <input v-model="personalData.name" type="text" placeholder="name" id="name">
                <label for="email">Email address</label>
                <input v-model="personalData.email" type="text" placeholder="email" id="email">
                <label for="phone">Phone Number</label>
                <input v-model="personalData.phone" type="text" placeholder="+79921229322" id="phone">
            </form>
            <p v-if="allFields" class="fields-warning">All fields is required</p>
            <button @click="goForward" class="nextstep">Next step</button>
        </div>
        <div v-if="currentStep === 2" class="content2">
            <h1>Select your plan</h1>
            <p class="content2-titlep">You have the option of monthly or yearly billing</p>
            <div v-if="!personalData.monthly" class="select-div">
                <div class="select-item" @click="selectOther(1)" :class="{'selected-item': personalData.selectedPlan == 1}"> 
                    <img src="/images/icon-arcade.svg" alt="img" class="select-img"> 
                    <h3>Arcade</h3>
                    <p>$9/mo</p>
                </div>
                <div class="select-item" @click="selectOther(2)" :class="{'selected-item': personalData.selectedPlan == 2}">
                    <img src="/images/icon-advanced.svg" alt="img" class="select-img">
                    <h3>Advanced</h3>
                    <p>$12/mo</p>
                </div>
                <div class="select-item" @click="selectOther(3)" :class="{'selected-item': personalData.selectedPlan == 3}"> 
                    <img src="/images/icon-pro.svg" alt="img" class="select-img">
                    <h3>Pro</h3>
                    <p>$15/mo</p>
                </div>
            </div>
            <div v-else class="select-div">
                <div class="select-item" @click="selectOther(1)" :class="{'selected-item': personalData.selectedPlan == 1}"> 
                    <img src="/images/icon-arcade.svg" alt="img" class="select-img"> 
                    <h3>Arcade</h3>
                    <p class="select-item-regp">$90/mo</p>
                    <p class="select-item-free">2 months free</p>
                </div>
                <div class="select-item" @click="selectOther(2)" :class="{'selected-item': personalData.selectedPlan == 2}">
                    <img src="/images/icon-advanced.svg" alt="img" class="select-img">
                    <h3>Advanced</h3>
                    <p class="select-item-regp">$120/mo</p>
                    <p class="select-item-free">2 months free</p>
                </div>
                <div class="select-item" @click="selectOther(3)" :class="{'selected-item': personalData.selectedPlan == 3}"> 
                    <img src="/images/icon-pro.svg" alt="img" class="select-img">
                    <h3>Pro</h3>
                    <p class="select-item-regp">$150/mo</p>
                    <p class="select-item-free">2 months free</p>
                </div>
            </div>
            <div class="check">
                <p>Monthly</p>
                <input type="checkbox" id="switch" class="toggle-input" v-model="personalData.monthly"/><label class="toggle-label" for="switch">Toggle</label>
                <p>Early</p>
            </div>
            <button @click="goBack" class="goback">Go back</button>
            <button @click="goForward" class="nextstep">Next step</button>
        </div>
        <div v-if="currentStep === 3" class="content3">
            <h1>Pick add-ons</h1>
            <p class="content3-titlep">Add-ons help</p>
            <div v-if="!personalData.monthly">
                <div class="content3-select-item" :class="{'content3-selected': personalData.addOns['onlineService']}">
                    <input v-model="personalData.addOns['onlineService']" class="content3-input" type="checkbox">
                    <div class="content3-text">
                        <h3>Online service</h3>
                        <p>Access to multiplayer games</p>
                    </div>
                    <p class="content3-price">+$1/mo</p>                    
                </div>
                <div class="content3-select-item" :class="{'content3-selected': personalData.addOns['largerStorage']}">
                    <input v-model="personalData.addOns['largerStorage']" class="content3-input" type="checkbox">
                    <div class="content3-text">
                        <h3>Larger storage</h3>
                        <p>Extra 1TB of cloud save</p>
                    </div>
                    <p class="content3-price">+$2/mo</p>
                </div>
                <div class="content3-select-item" :class="{'content3-selected': personalData.addOns['customizableProfile']}">
                    <input v-model="personalData.addOns['customizableProfile']" class="content3-input" type="checkbox">
                    <div class="content3-text">
                        <h3>Customizable profile</h3>
                        <p>Custom theme on your profile</p>
                    </div>
                    <p class="content3-price">+$2/mo</p>
                </div>
            </div>
            <div v-else>
                <div class="content3-select-item" :class="{'content3-selected': personalData.addOns['onlineService']}">
                    <input v-model="personalData.addOns['onlineService']" class="content3-input" type="checkbox">
                    <div class="content3-text">
                        <h3>Online service</h3>
                        <p>Access to multiplayer games</p>
                    </div>
                    <p class="content3-price">+$10/yr</p>                    
                </div>
                <div class="content3-select-item" :class="{'content3-selected': personalData.addOns['largerStorage']}">
                    <input v-model="personalData.addOns['largerStorage']" class="content3-input" type="checkbox">
                    <div class="content3-text">
                        <h3>Larger storage</h3>
                        <p>Extra 1TB of cloud save</p>
                    </div>
                    <p class="content3-price">+$20/yr</p>
                </div>
                <div class="content3-select-item" :class="{'content3-selected': personalData.addOns['customizableProfile']}">
                    <input v-model="personalData.addOns['customizableProfile']" class="content3-input" type="checkbox">
                    <div class="content3-text">
                        <h3>Customizable profile</h3>
                        <p>Custom theme on your profile</p>
                    </div>
                    <p class="content3-price">+$20/yr</p>
                </div>
            </div>
            <button @click="goBack" class="goback">Go back</button>
            <button @click="goForward" class="nextstep">Next step</button>
        </div>
        <div v-if="currentStep === 4" class="content4">
            <h1>Finishing up</h1>
            <p class="content4-titlep">Double-check everything looks OK before confirming.</p>
            <div>
                <div class="content4-blue">
                    <div class="content4-blue-item1">
                        <div>
                            <h3>{{ finalData.plan.name }}</h3>
                            <a href="##">Change</a>
                        </div>
                        <p>{{ finalData.plan.price }}</p>
                    </div>
                    <div v-for="item in finalData.addOns" class="content4-blue-item2">
                        <p class="content4-blue-botname">{{  item.name }}</p>
                        <p class="content4-blue-botprice">{{ item.price }}</p>
                    </div>
                    
                </div>
                <div class="content4-total">
                    <p class="total-name" v-if="!personalData.monthly">Total (per month)</p>
                    <p class="total-name" v-else>Total (per year)</p>
                    <p v-if="!personalData.monthly" class="total-price">+${{finalData.totalCount}}/mo</p>
                    <p v-else class="total-price">+${{finalData.totalCount}}/yr</p>
                </div>
            </div>
            <button @click="goBack" class="goback">Go back</button>
            <button class="confirm" @click="confirm">Confirm</button>
        </div>
        <div v-if="currentStep===5" class="content5">
            
                <img src="/images/icon-thank-you.svg" alt="Da">
                <h1>Thank you!</h1>
                <p>Thanks for confirming your subscription! We hope you have fun using our platform. If you ever need support, please feel free to email us at support@loremgaming.com. </p>
            
        </div>
    </div>
  </div>
</template>

<style>
    
</style>
