<template>
    <div class="add-invoice">
        <h2>New Invoice</h2>
        <div class="add-invoice__block">
            <div class="add-invoice__block-header">Bill From</div>
            <div class="add-invoice__input">
                <label class="add-invoice__label">
                    <span>Street Address</span>
                    <input type="text" v-model="addForm.frStreet">
                </label>
            </div>
            <div class="add-invoice__input add-invoice__input--twitter">
                <label class="add-invoice__label">
                    <span>City</span>
                    <input type="text" v-model="addForm.frCity">
                </label>
            </div>
            <div class="add-invoice__input add-invoice__input--twitter">
                <label class="add-invoice__label">
                    <span>Zip Code</span>
                    <input type="text" v-model="addForm.frZip">
                </label>
            </div>
            <div class="add-invoice__input add-invoice__input--twitter">
                <label class="add-invoice__label">
                    <span>Country</span>
                    <input type="text" v-model="addForm.frCountry">
                </label>
            </div>
        </div>
        <div class="add-invoice__block">
            <div class="add-invoice__block-header">Bill To</div>
            <div class="add-invoice__input">
                <label class="add-invoice__label">
                    <span>Client's Name</span>
                    <input type="text" v-model="addForm.toName">
                </label>
            </div>
            <div class="add-invoice__input">
                <label class="add-invoice__label">
                    <span>Client's Email</span>
                    <input type="text" v-model="addForm.toEmail">
                </label>
            </div>
            <div class="add-invoice__input">
                <label class="add-invoice__label">
                    <span>Street Address</span>
                    <input type="text" v-model="addForm.toStreet">
                </label>
            </div>
            <div class="add-invoice__input add-invoice__input--twitter">
                <label class="add-invoice__label">
                    <span>City</span>
                    <input type="text" v-model="addForm.toCity">
                </label>
            </div>
            <div class="add-invoice__input add-invoice__input--twitter">
                <label class="add-invoice__label">
                    <span>Zip Code</span>
                    <input type="text" v-model="addForm.toZip">
                </label>
            </div>
            <div class="add-invoice__input add-invoice__input--twitter">
                <label class="add-invoice__label">
                    <span>Country</span>
                    <input type="text" v-model="addForm.toCountry">
                </label>
            </div>
        </div>
        <div class="add-invoice__block">
            <div class="add-invoice__input add-invoice__input--half">
                <label class="add-invoice__label">
                    <span>Invoice Date</span>
                    <input type="text" v-model="addForm.date" readonly>
                </label>
            </div>
            <div class="add-invoice__input add-invoice__input--half">
                <label class="add-invoice__label">
                    <span>Payment Due</span>
                    <input type="text" v-model="addForm.due">
                </label>
            </div>
            <div class="add-invoice__input">
                <label class="add-invoice__label">
                    <span>Payment Terms</span>
                    <input type="text" v-model="addForm.terms">
                </label>
            </div>
            <div class="add-invoice__input">
                <label class="add-invoice__label">
                    <span>Product Description</span>
                    <input type="text" v-model="addForm.description">
                </label>
            </div>
        </div>
        <div class="add-invoice__block">
            <h3>Item List</h3>
            <items-list></items-list>
        </div>
        <div class="button-items">
            <button-item @click="$emit('closeModal')" theme="cancel">
                Cancel
            </button-item>
            <div class="button-items__right">
                <button-item>
                    Save Draft
                </button-item>
                <button-item @click="createInvoice" theme="create"> Create Invoice
                </button-item>
            </div>
        </div>
    </div>
</template>
<script>
    import ButtonItem from './buttonItem.vue'
    import ItemsList from './itemsList/itemsList.vue'
    export default {
        name: 'addInvoice',
        components: {
            ButtonItem,
            ItemsList
        },
        data() {
            return {
                addForm: {
                    frStreet: '',
                    frCity: '',
                    frZip: '',
                    frCountry: '',
                    toName: '',
                    toEmail: '',
                    toStreet: '',
                    toCity: '',
                    toZip: '',
                    toCountry: '',
                    date: new Date().toLocaleDateString("ru-RU"),
                    due: '',
                    terms: '',
                    description: ''
                }
            }
        },
        methods: {
            createInvoice() {
                let tmp = JSON.parse(localStorage.getItem("invoices"))
                tmp.push(this.addForm)
                localStorage.setItem('invoices', JSON.stringify(tmp))
                this.clearForm()
                this.addForm.date = new Date().toLocaleDateString("ru-RU")
            },
            clearForm() {
                Object.keys(this.addForm).forEach(i => {
                    this.addForm[i] = ''
                })
            }
        },
        created() {
        }

    }
</script>
<style lang="scss">
    .button-items {
        display: flex;
        justify-content: space-between;

        &__right {
            display: flex;
            justify-content: space-around;
        }
    }

    .add-invoice {
        h2 {
            margin-bottom: 48px;
        }

        &__block {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;

            &+& {
                margin-top: 40px;
            }

            &-header {
                width: 100%;
                color: #7c5dfa;
                font-size: 12px;
                margin-bottom: 24px;
            }
        }

        &__input {
            width: 100%;
            margin-bottom: 16px;

            &--twitter {
                width: 30%;
            }

            &--half {
                width: 48%;
            }
        }

        &__label {
            display: flex;
            flex-direction: column;

            span {
                font-size: 12px;
                margin-bottom: 6px;
            }

            input {
                width: 100%;
                color: #fff;
                background-color: #1e2139;
                border: none;
                border-radius: 4px;
                padding: 12px 4px;

                &:focus,
                &:focus-visible {
                    outline: none;
                }
            }
        }
    }
</style>