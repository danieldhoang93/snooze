<template>
  <q-page class="pageSize">
     <q-dialog v-model="showCharityPicker">  
        <q-card dark class="charityPickerWindow">
          <CharityPicker></CharityPicker>
            <q-card-actions align="right">
              <q-btn flat label="Cancel" color="accent" v-close-popup />
              <q-btn flat label="Ok" color="accent" v-close-popup />
            </q-card-actions>
        </q-card>
      </q-dialog>
    <div>
      <q-list clickable dark v-for="alarm in alarms" :key="alarm" @click="showAlarmDetails(alarm.time, alarm.label)">
        <q-item clickable v-ripple class="row alarmList">
          <div class="col-10 text-left q-pa-md alarmListItem">
            <div class="text-h3" :class="(alarm.status)?'enabled':'grey'">{{ alarm.time }}</div>
            <div class="text-caption2 grey">{{ alarm.label }}</div>
            <div class="row">
              <div v-for="day in alarm.days" :key="day" class="grey">{{ day }}&nbsp; </div>
            </div>
          </div>
          <div class="col-2 alarmListItem">
            <q-toggle v-model="alarm.status" color="accent"/>
          </div>
        </q-item>
        <q-separator spaced inset dark />
      </q-list>
    </div>
      <q-dialog v-model="showAlarmDetail">  
        <q-card dark class="alarmDetailsWindow">
            <Alarm :label="label" :alarmTime="alarmTime"></Alarm>
            <q-card-actions align="right">
              <q-btn flat label="Cancel" color="accent" v-close-popup />
              <q-btn flat label="Ok" color="accent" v-close-popup />
            </q-card-actions>
        </q-card>
      </q-dialog>

    <div>
      <q-btn unelevated round color="accent" icon="add" class="addButton" @click="showAlarmDetails()"/>
    </div>
    
  </q-page>
</template>


<script>
import Alarm from 'components/Alarm.vue' 
import CharityPicker from 'components/CharityPicker.vue' 

export default {
  components: {
    Alarm, CharityPicker
  },
  data() {
    return {
      showAlarmDetail: false,
      showCharityPicker:true,
      label: '',
      alarmTime:'',
      alarms: [
        {
          time: '10:55',
          status: true,
          label: 'everyday',
          days:['Mon', 'Tues']
        },
        {
          time: '16:00',
          status: false,
          label: 'nap',
          days:['Thurs', 'Fri']
        },
        {
          time: '07:00',
          status: false,
          label: 'nap',
          days:['Thurs', 'Fri']
        },
        {
          time: '08:00',
          status: false,
          label: 'nap',
          days:['Thurs', 'Fri']
        },
        {
          time: '19:00',
          status: false,
          label: 'nap',
          days:['Thurs', 'Fri']
        },
        {
          time: '10:00',
          status: false,
          label: 'nap',
          days:['Thurs', 'Fri']
        },
        {
          time: '11:00',
          status: false,
          label: 'nap',
          days:['Thurs', 'Fri']
        },
        {
          time: '12:00',
          status: false,
          label: 'nap',
          days:['Thurs', 'Fri']
        },
        {
          time: '03:00',
          status: false,
          label: 'nap',
          days:['Thurs', 'Fri']
        },
        {
          time: '14:00',
          status: false,
          label: 'nap',
          days:['Thurs', 'Fri']
        }
      ]
    }
  },
  methods: {
    showAlarmDetails(time, label) {
      this.showAlarmDetail = !this.showAlarmDetail;
      this.alarmTime = time;
      this.label = label;
    }
  }
}
</script>

<style lang="scss" scoped>
.pageSize {
  width:600px;
  color:white;
  margin:auto;
  justify-content: center;
  align-items:center;
  text-align: center;
  background:rgb(14, 14, 14);
}

div {
 // border:1px solid red;
}

.alarmList {
  height:150px;
  margin-top:auto;
  margin-bottom:auto;

  .alarmListItem {
    justify-content:center;
    margin-top:auto;
    margin-bottom:auto;
  }
}

.alarmDetailsWindow {
  width:400px;
  height:700px;
}

.charityPickerWindow {
  width:400px;
  height:700px;
}

.grey {
  color: rgb(87, 87, 87);
}

.enabled {
  color: white;
}

.addButton {
  position: fixed;
  top: 85vh;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

@media screen and (max-width: 600px) {
  .pageSize {
    width:100%;
    
  }
}
</style>