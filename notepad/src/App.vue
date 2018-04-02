<template>
  <div id="app">
    <div class="card w-25 user-input" >      
      <div class="card-body">
        <h5 class="card-title">Add your note</h5>
        <select class="mb-3" v-model="selectedtype">
          <option v-for="nt in notetypes" :key="nt">{{nt}}</option>
        </select>
        <br>
        <textarea class="msg" v-model="message" placeholder="please enter the information here......"></textarea>
        <br>
        <button class="btn btn-primary">Submit</button>
      </div>
    </div>
   <div class="list-group w-25">
    <div class="w-100 mb-3 list-group-item" v-for="note in notes" :key="note.id">
      <h5>{{note.nt}}</h5>
      <p>{{note.msg}}</p>
      <small>{{note.date}}</small>
    </div>
  </div>
  <!--<div class="datepicker-trigger">
      <input
        type="text"
        id="datepicker-trigger"
        placeholder="Select dates"
        :value="formatDates(dateOne, dateTwo)"
      >

      <AirbnbStyleDatepicker
        :trigger-element-id="'datepicker-trigger'"
        :mode="'range'"
        :fullscreen-mobile="true"
        :date-one="dateOne"
        :date-two="dateTwo"
        @date-one-selected="val => { dateOne = val }"
        @date-two-selected="val => { dateTwo = val }"
      />
    </div>-->
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      notetypes: ['To Do','Expense'],
      selectedtype: [],
      notes: [
        {
          id: 1,
          nt: "To Do",
          msg: "Check sth",
          date: "15/11/2016 04:34 AM",
        },
         {
          id: 2,
          nt: "To Do",
          msg: "Check sth",
          date: "15/11/2016 04:34 AM",
        }
      ],
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
