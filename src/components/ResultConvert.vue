<template>
    <ion-card>
        <ion-card-header>
            <ion-card-title>{{ currencySelected }}</ion-card-title>
            <ion-card-subtitle>{{ amount }} EUR to {{currencyCodeSelected}}</ion-card-subtitle>
        </ion-card-header>
        <ion-card-content v-if="currencyResult">
            {{ result }}
        </ion-card-content>
    </ion-card>
</template>

<style scoped>

    .collapse{
        height: 0px;
        overflow: hidden;
        transition: 0.5s linear ;
    }

    .open{
        height: auto;
    }

    button{
        outline: none;
        background: none;
    }

</style>
<script>
    export default {
        name: "converted-result",
        props: {
            currencySelected: {
                type: String,
            },
            currencyCodeSelected: {
                type: String,
            },
            currencyResult: {
                type: String
            },
            amount: {
                type: Number
            },
        },
        data() {
            return {
                open: false
            }
        }
    }
</script>