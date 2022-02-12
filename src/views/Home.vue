<template>
  <div class="container w-50-lg p-2 border-primary border border-1 rounded-2 shadow-sm">
    <form class="main-form">
      <div class="mb-3 d-flex justify-content-evenly flex-wrap">
        <div>
          <label for="DPIRadio" class="form-label fw-bold">DPI</label>
        </div>
        <template v-for="i in dpiRange" :key="i">
          <div class="form-check form-check-inline">
            <input
              class="form-check-input"
              type="radio"
              v-model="dpi"
              :name="'radio_dpi_' + i"
              :id="'radio_dpi_' + i"
              :value="i"
              :checked="i === 96"
            />
            <label class="form-check-label" :for="'radio_dpi_' + i">{{i}}</label>
          </div>
        </template>
      </div>

      <div class="mb-3">
        <div class="d-flex justify-content-center">
          <div class="form-check form-switch">
            <input class="form-check-input" type="checkbox" id="px2cmiSwitch" v-model="px2cmi">
            <label class="form-check-label mx-3" for="px2cmiSwitch">
              <span class="text-info fw-bold">
                {{ px2cmi === true ? 'pixel to cm / inch' : 'cm / inch to pixel'}}
              </span> Mode</label>
          </div>
        </div>
      </div>

      <div class="mb-3 d-flex justify-content-evenly align-items-center">
        <label for="c-width" class="col-sm-2 col-form-label fw-bold">Width</label>
        <div class="w-25">
          <input type="number" class="form-control" id="c-width" style="font-size:20px" v-model="width_input"/>
        </div>
        <label for="c-height" class="col-sm-2 col-form-label fw-bold">Height</label>
        <div class="w-25">
          <input type="number" class="form-control" id="c-height" style="font-size:20px" v-model="height_input" />
        </div>
      </div>
    </form>

    <div v-show="px2cmi !== true">
      <div class="btn-group" role="group" aria-label="Basic radio toggle button group">
        <input type="radio" class="btn-check" name="btnradio" id="cmi2px_A4" 
          @click="height_input=29.7;width_input=21">
        <label class="btn btn-outline-primary" for="cmi2px_A4">A4</label>

        <input type="radio" class="btn-check" name="btnradio" id="cmi2px_pc"
          @click="height_input=14.8;width_input=10.5">
        <label class="btn btn-outline-primary" for="cmi2px_pc">PostCard</label>

        <input type="radio" class="btn-check" name="btnradio" id="cmi2px_46p"
          @click="height_input=4;width_input=6">
        <label class="btn btn-outline-primary" for="cmi2px_46p">4×6 Photo</label>
      </div>
    </div>

    <ConvertedTable 
      :px2cmi="px2cmi" 
      :whWrapper="{width: width_input, height: height_input}"
      :dpi="dpi"
      :inchToCm="inchToCm"
    />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import ConvertedTable from '@/components/ConvertedTable.vue'

export default {
  name: "Home",
  data() {
    return {
      dpiRange: [72, 96, 150, 300],
      dpi: 96,
      inchToCm: 2.54,
      height_input: 1080,
      width_input: 1920,
      px2cmi: true
    }
  },
  components: {
    ConvertedTable
  },
  computed: {

  }

};
</script>

<style lang="scss" scoped>
.main-form {
  font-size: 22px;
}

.w-50-lg {
    @media screen and (min-width:992px){    
      width: 50% !important;
    }
}
</style>
