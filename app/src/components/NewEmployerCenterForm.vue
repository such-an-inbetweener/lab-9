<template>
 <form
        v-on:submit.prevent="addNewEmployerCenter"
        class="newForm"
        v-if="showNewEmployerCenterForm"
      >
        Імя: <input v-model="newEmployerCenter.nameandsurname" /><br />
        Стать: <input v-model="newEmployerCenter.sex" /> <br />

        Дата народження: <input type="number" v-model.number="newEmployerCenter.birthdate" /> <br />
        Освіта: <input type="number" v-model.number="newEmployerCenter.education" /> <br />
        Спеціальність: <input type="number" v-model.number="newEmployerCenter.speciality" /> <br />
        Дата обліку: <input type="number" v-model.number="newEmployerCenter.accountdate" /> <br />

        <button type="submit">Додати</button>
        <button type="reset">Очистити</button>
      </form>
</template>

<script>
export default {
  name: "NewEmployerCenterForm",
  props: {
    modelValue: Object,
  },
  data() {
    return {
        showNewEmployerCenterForm:false,
        newEmployerCenter : this.modelValue,
    };
  },
   methods:{
        
        addNewEmployerCenter(){
            this.$emit("update:modelValue", this.newEmployerCenter); 
            this.hide();
        }, 
        show(){
            this.showNewEmployerCenterForm = true;
        },
        hide(){
            this.showNewEmployerCenterForm = false;
        }
    }, 
};
</script>

<style scoped>
</style>>
