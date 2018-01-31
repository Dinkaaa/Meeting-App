<template>
  <div class='SelectDateTimeComponent'>
    <span>Select Start and End datetime</span>
    <date-picker v-model="value1" range 
                type="datetime" 
                format="yyyy-MM-dd HH:mm" 
                lang="en"
                :not-before="this.notBefore"
                >
    </date-picker>
  </div>
</template>

<script>
import DatePicker from 'vue2-datepicker'

export default {
  components: { DatePicker },
  data() {
    return {
      value1: '',
      notBefore: new Date,
      shortcuts: [
        {
          start: new Date(),
          end: new Date()
        }
      ]
    }
  },
  watch: {
      'value1'() {
          this.dateHandler(this.value1);
      }
  },
  methods:{
      dateHandler(value){
          this.$emit('setDataTime', value);
      }
  }
}
</script>


