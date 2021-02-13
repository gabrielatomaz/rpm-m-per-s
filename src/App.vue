<template>
  <div id="app" class="mt-5">
      <Banner title="Formulas">
        v = rpm * 2 * π * r / 60 
        <br />
        rpm = (v * 60) / (2 * π * r)
      </Banner>
      <div class="columns is-mobile is-centered">
        <div class="column is-half mt-5">
        <div class="field">
          <div class="field-body m-2">
            <Input
              type="number"
              placeholder="RPM"
              v-model="rpm"
            />
          </div>
          <div class="field-body m-2">
            <Input
              type="number"
              placeholder="Wheel radius"
              v-model="wheelRadius"
            />
          </div>
          <div class="field-body m-2">
            <Input
              type="number"
              placeholder="m/s"
              v-model="mPerS"
            />
          </div>
          <div class="field-body m-2">
            <Button :disabled="calculateIsDisabled" text="Calculate" :event="calculate" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Input, Button, Banner } from './components'

export default {
  name: 'App',

  components: {
    Input,
    Button,
    Banner,
  },

  data() {
        return {
            rpm: '',
            mPerS: '',
            wheelRadius: '',
        }
  },

  computed: {
    calculateIsDisabled() {
      return (!this.wheelRadius && !this.mPerS && !this.rpm) ||
              (!this.wheelRadius && !this.mPerS && !!this.rpm) || 
              (!this.wheelRadius && !!this.mPerS && !this.rpm) || 
              (!!this.wheelRadius && !!this.mPerS && !!this.rpm) ||
              (!!this.rpm && !!this.mPerS);
    },
  },

  methods: {
    calculate() {
      if (!this.mPerS) this.mPerS = this.rpm * 2 * Math.PI * this.wheelRadius / 60
      else this.rpm = (this.mPerS * 60) / (2 * Math.PI * this.wheelRadius)
    },
  }
}
</script>
