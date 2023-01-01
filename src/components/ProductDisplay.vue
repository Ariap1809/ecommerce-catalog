<template>
    <div v-if="loading">
        <div class="view">
            <div class="loader"></div>
        </div>
    </div>

    <div v-else>
        <div v-if="!category.unavaliable" class="view">
            <WebBackground :dataComponent=category />
            <div class="card">
                <div class="imageBox">
                    <img :src="data.image" />
                </div>
                <div class="textContainer">
                    <div class="headingBox">
                        <div :class="{ colorPalletteWoman: category.woman, colorPalletteMan: category.man, }">
                            {{ data.title }}
                        </div>
                    </div>
                    <div class="categoryBox">
                        <div class="container">
                            <div class="category">{{ data.category }}</div>
                            <RatingComponent :woman="category.woman" :man="category.man" :rating="data.rating.rate" />
                        </div>
                    </div>
                    <div class="descriptionBox">
                        {{ data.description }}
                    </div>
                    <div class="footerBox">
                        ${{ data.price }} <br />
                        <div class="buttonContainer">
                            <div class="buttonItem">
                                <BuyButton :woman="category.woman" :man="category.man" />
                            </div>
                            <div v-if="category.woman" class="buttonItem">
                                <button type="button" @click="getProductFromAPI()" class="customNextButtonWoman">Next
                                    Product</button>
                            </div>
                            <div v-else class="buttonItem">
                                <button type="button" @click="getProductFromAPI()" class="customNextButtonMan">Next
                                    Product</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div v-else class="unavaliableView">
            <WebBackground :dataComponent=category />
            <div class="unavaliableCard">
                This product is unavaliable to show
                <button type="button" @click="getProductFromAPI()" class="customNextButton">Next
                    Product</button>
            </div>

        </div>
    </div>
</template>
<script>
import RatingComponent from "./RatingComponent.vue";
import BuyButton from "./BuyButton.vue";
import WebBackground from "./WebBackground.vue";
export default {
    name: "ProductDisplay",
    components: {
        RatingComponent,
        BuyButton,
        WebBackground
    },
    data() {
        return {
            title: 'data',
            data: null,
            category:
            {
                man: null,
                woman: null,
                unavaliable: null,
            },
            loading: false,
            index: 1
        }
    },
    methods:
    {
        async getProductFromAPI() {
            if (this.index == 21) {
                this.index = 1;
            }
            this.loading = true;
            const api = await fetch(`https://fakestoreapi.com/products/${this.index}`);
            const response = await api.json();
            const data = response;
            let product = { ...data }
            this.index++;
            if (product.category === "men's clothing") {
                this.category.man = true;
                this.category.woman = false;
                this.category.unavaliable = false;
            }
            else if (product.category === "women's clothing") {
                this.category.man = false;
                this.category.woman = true;
                this.category.unavaliable = false;
            }
            else {
                this.category.man = false;
                this.category.woman = false;
                this.category.unavaliable = true;
            }
            this.data = data;
            console.log(data);
            console.log(this.category)

            this.loading = false;

        }
    },
    mounted() {

        this.getProductFromAPI();

    }
};

</script>

<style scoped>
/* Color Pallette CSS */

.colorPalletteWoman {
    color: #720060;
}

.colorPalletteMan {
    color: #002772;
}

/* Unavaliable View CSS */

.unavaliableView {
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

.unavaliableCard {
    box-shadow: 0 4px 10px 0 rgba(0, 0, 0, 0.2);
    background-color: white;
    width: 82%;
    height: 70%;
    display: flex;
    text-align: center;
    justify-content: center;
    flex-direction: column;
    font-family: "Prompt", sans-serif;
    font-weight: 550;
    font-size: 1.2rem;
    background-image: url("../assets/sad-face.svg");
    background-position: center;
    background-repeat: no-repeat;
}

/* Normal View CSS */

.view {
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

.card {
    box-shadow: 0 4px 10px 0 rgba(0, 0, 0, 0.2);
    background-color: white;
    width: 82%;
    height: 70%;
    display: flex;
}

.imageBox {
    flex: 2;
    display: flex;
    align-items: center;
    justify-content: center;
    box-sizing: border-box;
}

.imageBox img {
    max-width: 80%;
    max-height: 80%;
}

.textContainer {
    flex: 3;
    box-sizing: border-box;
    padding: 15px;
    display: flex;
    flex-direction: column;
}

.headingBox {
    flex: 2;
    font-family: "Prompt", sans-serif;
    font-weight: 550;
    font-size: 2rem;
    line-height: 1.2;
    display: flex;
}

.categoryBox {
    flex: 1;
    font-family: "Prompt", sans-serif;
}

.container {
    width: 100%;
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    padding-bottom: 10px;
    border-bottom: 2px solid rgb(206, 206, 206);
}

.descriptionBox {
    flex: 4;
    font-family: "Prompt", sans-serif;
    line-height: 1.2;
    font-size: 1.2rem;
}

.footerBox {
    border-top: 2px solid rgb(206, 206, 206);
    padding-top: 10px;
    flex: 2;
    font-family: "Prompt", sans-serif;
    font-weight: 575;
    font-size: 1.4em;
}

.buttonContainer {
    display: flex;
}

.buttonItem {
    flex: 1;
}

/* Next Button */


.customNextButtonWoman {
    border: 2px solid #720060;
    background-color: white;
    font-family: "Prompt", sans-serif;
    font-weight: 700;
    color: #720060;
    padding: 10px;
    margin-right: 20px;
    margin-top: 20px;
    width: 90%;
    border-radius: 5px;
}

.customNextButtonMan {
    border: 2px solid #002772;
    background-color: white;
    font-family: "Prompt", sans-serif;
    font-weight: 700;
    color: #002772;
    padding: 10px;
    margin-right: 20px;
    margin-top: 20px;
    width: 90%;
    border-radius: 5px;
}

.customNextButton {
    border: 2px solid black;
    background-color: white;
    font-family: "Prompt", sans-serif;
    font-weight: 700;
    color: black;
    padding: 10px;
    margin-right: 25%;
    margin-left: 25%;
    margin-top: 20px;
    width: 50%;
    border-radius: 5px;
}



/* Loader  */

.view {
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

.loader {
    border: 16px solid #f3f3f3;
    border-radius: 50%;
    border-top: 16px solid #3498db;
    width: 120px;
    height: 120px;
    animation: spin 2s linear infinite;
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
</style>
