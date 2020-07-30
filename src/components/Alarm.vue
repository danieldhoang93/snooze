<template>
    <div class="alarmDetailLayout">
        <div>
            <q-time dark color="accent"
                    text-color="black" 
                    flat
                    v-model="alarmTime"
                    class="clock"/>

        
            
        </div>
        <q-input dark borderless v-model="label" label-color="white" label="Label" class="q-pa-md" dense></q-input>
        <q-input dark borderless v-model="sound" label-color="white" label="Alarm Sound" class="q-pa-md" dense />
        <div class="dayButtons">
            <div>
                <q-btn unelevated size="md" round dark class="q-mr-xs" :class="sun ?'daySelected':'dayUnselected'" @click="sun = !sun">Su</q-btn>
                <q-btn unelevated size="md" round dark class="q-mx-xs" :class="mon ?'daySelected':'dayUnselected'" @click="mon = !mon">M</q-btn>
                <q-btn unelevated size="md" round dark class="q-mx-xs" :class="tue ?'daySelected':'dayUnselected'" @click="tue = !tue">T</q-btn>
                <q-btn unelevated size="md" round dark class="q-mx-xs" :class="wed ?'daySelected':'dayUnselected'" @click="wed = !wed">W</q-btn>
                <q-btn unelevated size="md" round dark class="q-mx-xs" :class="thu ?'daySelected':'dayUnselected'" @click="thu = !thu">Th</q-btn>
                <q-btn unelevated size="md" round dark class="q-mx-xs" :class="fri ?'daySelected':'dayUnselected'" @click="fri = !fri">F</q-btn>
                <q-btn unelevated size="md" round dark class="q-ml-xs" :class="sat ?'daySelected':'dayUnselected'" @click="sat = !sat">Sa</q-btn>
            </div>
        </div>
       
    </div>
</template>

<script>
import Alarm from 'components/Alarm.vue' 

export default {
  components: {
    Alarm
  },
  props: ['alarmTime', 'label'],
  data() {
    return {
      sun:false,
      mon:false,
      tue:false,
      wed:false,
      thu:false,
      fri:false,
      sat:false,
      time:''
    }
  }
}
</script>

<style lang="scss">
.alarmDetailLayout {
    background: #1D1D1D;
    height: 92.5%;
}

.clock {
    position:relative;
    height:400px;
    top: 50%;
    left: 50%;
    margin-right: -50%;
    transform: translate(-50%, 10%) 
}

.dayButtons {
  width:100%;
  margin-top:25px;
  display: flex;
  justify-content: center;
}

.daySelected {
    background-color:#5c5efc;
    color:white;
}

.dayUnselected {
    color:rgb(66, 66, 66);
}
</style>