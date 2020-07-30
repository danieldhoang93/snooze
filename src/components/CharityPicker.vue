<template>
    <div class="charityPickerLayout q-pa-md">
        <div class="text-h5">Charity</div>
        <div class="q-pt-md">
            Pick a charity to donate to from the list below! Everytime you snooze this alarm, money will go toward the charity selected at 10$ intervals.
        </div>

        <div class="q-pt-md charityDropdown">
            <q-btn-dropdown color="primary" label="Select A Charity">
                <q-list v-for="charity in charityList" :key="charity">
                    <q-item clickable v-close-popup>
                        <q-item-section>
                            <q-item-label>{{ charity.name }}</q-item-label>
                        </q-item-section>
                    </q-item>
                </q-list>
            </q-btn-dropdown>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      selectedCharity: 'Human Rights Watch',
      charityList: [
        {
            name:'Human Rights Watch'
        }, 
        {
            name: 'United Way'
        }, 
        {
            name: 'Feeding America'
        }, 
        {
            name: 'Salvation Army'
        }
        ]
    }
  }
}
</script>

<style lang="scss">
.charityPickerLayout {
    background: #1D1D1D;
}

.charityDropdown {
    width:100%;
}
</style>