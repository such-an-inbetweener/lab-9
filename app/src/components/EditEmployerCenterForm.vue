<template>
     <form
        v-on:submit.prevent="eeditSelectedEmployerCenter"
        class="newForm"
        v-if="showEditEmployerCenterForm"
      >
        Адреса: <input v-model="editEmployerCenter.adress" /><br />
        Власник: <input v-model="editEmployerCenter.firm_owner" /> <br />

        Залишок А80: <input type="number" v-model.number="editEmployerCenter.rest_A80" /> <br />
        Залишок А92: <input type="number" v-model.number="editEmployerCenter.rest_A92" /> <br />
        Залишок А95: <input type="number" v-model.number="editEmployerCenter.rest_A95" /> <br />

        Ціна А80: <input type="number" v-model.number="editEmployerCenter.price_A80" /> <br />
        Ціна А92: <input type="number" v-model.number="editEmployerCenter.price_A92" /> <br />
        Ціна А95: <input type="number" v-model.number="editEmployerCenter.price_A95" /> <br />

        <button type="submit">Редагувати</button>
        <button type="reset">Очистити</button>
      </form>
</template>

<script>
export default {
    name:"EditEmployerCenterForm", 
    props:{
        modelValue: Object
    },
    data(){
      return {
          showEditEmployerCenterForm: false,
          editEmployerCenter: this.modelValue
      } 
    },
    methods:{
        eeditSelectedEmployerCenter(){
            this.$emit("update: modelValue", this.editEmployerCenter);
            this.hide();
        },
        show(editEmployerCenter){
            this.editEmployerCenter=editEmployerCenter;
            this.showEditEmployerCenterForm=true;
        },
        hide(){
            this.showEditEmployerCenterForm=false;
        }
    }
}
</script>