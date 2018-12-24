<template>
  <div
    id="app"
    >
    <full-calendar
      v-model="value"
      :dark="darkMode"
      label="Choose date time"
      inline
      schedule="test"
      v-on:changMonth="getmonthyear"
    />

    </div>

</template>

<script>
  import FullCalendar from './VueCtkDateTimePicker'
  export default {
    name: 'App',
    components: {
      FullCalendar
    },
    props: {
      formChild: ''
    },
    data () {
      return {
        devMode: false,
        value: this.formChild,
        rangeValues: {
          start: '2018-04-05',
          end: '2018-04-20'
        },
        rangeValues2: {
          start: null,
          end: null
        },
        timePickerValue: '14:26',
        minuteInterval: 5,
        minuteInterval2: 10,
        hint: 'Error message',
        errorHint: true,
        timeFormat: 'hh:mm a',
        minDate: '2018-04-03',
        maxDate: '2018-04-12',
        darkMode: false,
        shortcutsTranslation: {
          'this_week': 'Cette semaine',
          'last_30_days': '30 derniers jours',
          'last_month': 'Mois précédent',
          'last_year': 'L\'année dernière'
        },
        disabledDates: ['2018-04-03', '2018-04-07', '2018-04-09', '2018-04-11', '2018-04-13', '2018-04-15', '2018-04-17', '2018-04-19'],
        disabledHours: Array.from(new Array(8), (x, i) => `0${i}`).concat(
          Array.from(new Array(23), (x, i) => {
            if (i + 1 > 18) {
              return `${i + 1}`
            } else {
              return null
            }
          })
        )
      }
    },
    methods: {
      getmonthyear(monthlyyear){
        this.value = monthlyyear

      }
    }

  }
</script>

<style lang="scss">
  @import "./VueCtkDateTimePicker/assets/main.scss";
  html, body, #app, #vueCtkDateTimePicker {
    margin: 0;
    min-height: 100%;
    min-width: 100%;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    &.dark {
      background-color: darken(#424242, 20%);
      header {
        color: #ffffffb3;
      }
    }
  }
  header {
    text-align: center;
  }
  *, *::before, *::after {
    box-sizing: border-box;
  }
  img {
    height: 140px;
  }
  h3, h1, p {
    margin-top: 0;
  }
  .component-container {
    margin: 0 10px 20px 10px;
    padding: 20px;
    background: #F2F2F2;
    border-radius: 4px;
    box-shadow: 0 2px 1px -1px rgba(0, 0, 0, 0.2), 0 1px 1px 0 rgba(0, 0, 0, 0.14), 0 1px 3px 0 rgba(0, 0, 0, 0.12);
    &.dark {
      background-color: darken(#424242, 10%);
      color: #FFF;
      textarea {
        background: #424242;
        color: dodgerblue;
      }
    }
  }
  textarea {
    background-color: #FFF;
    color: #bd4147;
    border: 1px solid #CCC;
    border-radius: 4px;
    outline: none;
    font-size: 85%;
    width: 100%;
    font-weight: 700;
    font-family: monospace, monospace;
    resize: none;
  }
  .btn {
    padding: 10px 20px;
    margin-bottom: 20px;
    border: none;
    border-radius: 30px;
    font-size: 14px;
    outline: none;
    cursor: pointer;
    -webkit-transition: all 0.25s cubic-bezier(0.645, 0.045, 0.355, 1);
    background-color: #96bf31;
    color: #FFF;
    font-weight: 500;
    &:hover {
      background-color: darken(#96bf31, 10%);
    }
  }
  @media screen and (max-width: 1024px) {
    .components-container.flex {
      -webkit-flex-direction: column;
      -ms-flex-direction: column;
      flex-direction: column;
      flex-flow: column;
      -moz-flex-direction: column;
    }
  }
</style>
