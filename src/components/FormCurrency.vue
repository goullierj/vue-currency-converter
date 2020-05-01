<template>
    <form>
        <ion-item>
            <ion-label position="stacked">Amount</ion-label>
            <ion-input placeholder="EUR" :value="amount" @input="amount = $event.target.value"></ion-input>
        </ion-item>

        <ion-item>
            <ion-label>To</ion-label>
            <ion-select @ionChange="values = $event.target.value">
                <ion-select-option v-for="(currencyChoice, index) in currencyChoices" :key="index" :value="[currencyChoice, index]">{{ currencyChoice }} - {{ index }}</ion-select-option>
            </ion-select>
        </ion-item>

        <ion-button expand="block" @click.prevent="submitForm()">CONVERT</ion-button>
    </form>
</template>

<script>

    export default {
        name: "currency-form",
        components: {
        },
        data() {
            return {
                currencyChoices: {},
                result: '',
                amount: null,
                values: ''
            }
        },
        mounted () {
            this.axios
                .get('http://data.fixer.io/api/symbols?access_key=6743d70853ea3262e03545bc49897a2b&format=1')
                .then((response) => {
                    this.currencyChoices = response.data.symbols

                })
        },
        methods: {
            submitForm() {
                this.axios
                        .get('http://data.fixer.io/api/latest?access_key=6743d70853ea3262e03545bc49897a2b')
                        .then((response) => {
                            this.result = response.data.rates
                        })
                }
            }
        }
</script>
