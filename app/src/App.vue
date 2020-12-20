
<template>
  <div>
    
    Вибрано станцію {{ selected }}
    <input type="button" value="Додати" v-on:click="showForm" />
    <input type="button" value="Редагувати" v-on:click="showEditForm" />
    <input type="button" value="Вилучити" v-on:click="deleteEmployerCenter" />
    <input type="button" value="Знайти" v-on:click="showFindEmployerCenterOwner" />
    <div class="wrap">
     <new-gas-station-form v-model="newEmployerCenter" @submit.prevent="addNewEmployerCenter" ref="newEmployerCenterForm">
     </new-gas-station-form>

     <edit-gas-station-form 
      v-model="editEmployerCenter"
      @submit.prevent="editSelectedEmployerCenter"
      ref="editEmployerCenterForm"
     > </edit-gas-station-form>

      <find-gas-station-form
      v-model="findEmployerCenterOwner"
      @submit.prevent="findEmployerCenterOwner" 
      ref="FindEmployerCenterForm"
      > </find-gas-station-form>
        <form
        v-on:submit.prevent="findEmployerCenterOwner"
        class="newForm"
        v-if="showFindEmployerCenterForm"
      >
        Власник: <input type="text" v-model="firm_owner"> <br>

        <button type="submit">Знайти</button>
        <button type="reset">Очистити</button>
      
      </form>
      <ul>
        <gas-station-template
          v-for="(g, i) in EmployerCenters"
          :key="i"
          class="station"
          v-on:click="selectEmployerCenter(i)"
          :style="i == selected ? 'border:5px solid black' : ''"
          v-bind:EmployerCenter="g"
        >
        </gas-station-template>
      </ul>
    </div>
  </div>
</template>

<script>
import EditEmployerCenterForm from './components/EditEmployerCenterForm.vue';
import EmployerCenterTemplate from './components/EmployerCenterTemplate.vue';
import NewEmployerCenterForm from './components/NewEmployerCenterForm.vue';

export default {
  components: { 
    EmployerCenterTemplate,
    NewEmployerCenterForm,
    EditEmployerCenterForm },
  name: "App",
  data() {
    return {
      selected: -1,
      showNewEmployerCenterForm: false,
      showEditEmployerCenterForm: false,
      showFindEmployerCenterForm: false,
      EmployerCenter: {
          nameandsurname: "Ваня",
          sex: "m",
          birthdate: "1975 1 23",
        education: "Вища",
        speciality: "Математика",
        accountdate: "2010 5 30",
        },
      employerCenters: [
        {
          nameandsurname: "Ваня",
          sex: "m",
          birthdate: "1975 1 23",
        education: "Вища",
        speciality: "Математика",
        accountdate: "2010 5 30",
        },
        {
          nameandsurname: "Олена",
          sex: "f",
          birthdate: "1958 8 30",
        education: "Вища",
        speciality: "Математика",
        accountdate: "2005 3 5",
        },
        {
          nameandsurname: "Вася",
          sex: "m",
          birthdate: "1988 4 17",
          education: "Вища",
        speciality: "Математика",
          accountdate: "2008 5 7",
        },
      ],
      newEmployerCenter: {
          nameandsurname: "Ваня",
          sex: "m",
          birthdate: "1975 1 23",
        education: "Вища",
        speciality: "Математика",
        accountdate: "2010 5 30",
        },
      editEmployerCenter: {
          nameandsurname: "Ваня",
          sex: "m",
          birthdate: "1975 1 23",
        education: "Вища",
        speciality: "Математика",
        accountdate: "2010 5 30",
        },
     
    };
  },

  methods: {
    
    addNewEmployerCenter() {
      let newEmployerCenterCopy = Object.assign({}, this.newEmployerCenter);
      this.EmployerCenters.push(newEmployerCenterCopy);
      this.showNewEmployerCenterForm = false;},

    showForm() { this.$refs.newEmployerCenterForm.show(); },

    selectEmployerCenter(index) { this.selected = index; },

    showEditForm() {
      if (this.selected>=0){
        this.editEmployerCenter = this.EmployerCenters[this.selected];
        this.$refs.editEmployerCenterForm.show(this.editEmployerCenter);
      }
      else alert("Виберіть людину")
    },

    deleteEmployerCenter() { if (this.selected >= 0) this.EmployerCenters.splice(this.selected, 1);},
    
     showFindEmployerCenterOwner(){
      this.showFindEmployerCenterForm = !this.showFindEmployerCenterForm;
    },
    findEmployerCenterOwner(){
      var n_a = this.nameandsurname;
      let date = "";
      var info=this.employerCenter.filter(x=>x.nameandsurname===n_a);

      for(var i = 0; i < info.length; i++){
        date+=info[i].accountdate*1;
        
        }
        alert("дата обліку - "+date+" Імя - "+n_a);
      this.showFindWorkerForm=false;
    },
  },
};
</script>



<style scoped>

.station {
  background:goldenrod;
  width: 200px;
  position: relative;
  float: left;
}

</style>

