<template>
  <div id="app">
    <div class="card w-25 user-input" >      
      <div class="card-body">
        <h5 class="card-title">Add your note</h5>
        <select class="mb-3" v-model="selectedtype">
          <option v-for="nt in notetypes" :key="nt">{{nt}}</option>
        </select>
        <div class="datepicker-trigger" v-show="selectedtype === 'To Do'">
          <input
            type="text"
            id="datepicker-trigger"
            placeholder="Select dates"
            :value="formatDates(dateOne, dateTwo)"
          >
          <AirbnbStyleDatepicker
            :trigger-element-id="'datepicker-trigger'"
            :mode="'single'"
            :fullscreen-mobile="false"
            :date-one="dateOne"
            :months-to-show="1"
            @date-one-selected="val => { dateOne = val }"
          />
        </div>
        <br>
        <textarea class="msg" v-model="message" placeholder="please enter the information here......"></textarea>
        <br>
        <button class="btn btn-primary" @click="addNote(selectedtype,dateOne,message)">Submit</button>
        <p>{{dateOne}}</p>
      </div>
    </div>
   <div class="list-group w-25">
    <div class="w-100 mb-3 list-group-item" v-for="note in notes">
      <h5>{{note.msgType}}</h5>
      <p>{{note.msg}}</p>
      <small>{{note.date}}</small>
    </div>
  </div>
  </div>
</template>

<script>
import format from 'date-fns/format'

export default {
  name: 'app',
  data () {
    return {
      dateFormat: 'D MMM',
      dateOne: '',
      dateTwo: '',
      message: '',
      notetypes: ['To Do','Expense'],
      selectedtype: [],
      isshowdp: false,
      notes: [],
    }
  },
  methods: {
    formatDates(dateOne, dateTwo) {
      let formattedDates = ''
      if (dateOne) {
        formattedDates = format(dateOne, this.dateFormat)
      }
      if (dateTwo) {
        formattedDates += ' - ' + format(dateTwo, this.dateFormat)
      }
      return formattedDates
    },
    showdp(selectedtype){
      console.log("you have chosen " + selectedtype);
      if(selectedtype === "To Do"){
          isshowdp = true;
      }
    },
    addNote(selectedtype,dateOne,message){
      this.notes.push({msgType: selectedtype, date: dateOne, msg: message });
    }
  }
}
</script>

<style>
.user-input, .list-group{
  margin: auto;
  margin-bottom: 10px;
  margin-top: 30px;
}

.msg{
  width: 97.5%;
}
</style>
