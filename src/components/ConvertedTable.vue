<template>
<table class="table" style="font-size:20px">
      <thead>
        <tr class="border-primary">
          <th>Unit</th>
          <th>Width</th>
          <th>Height</th>
        </tr>
      </thead>
      <tbody>
        <tr v-show="px2cmi">
          <td>cm</td>
          <td>{{ (whWrapper.width / dpi * inchToCm).toFixed(3) }}</td>
          <td>{{ (whWrapper.height / dpi * inchToCm).toFixed(3) }}</td>
        </tr>
        <tr v-show="px2cmi">
          <td>inch</td>
          <td>{{ (whWrapper.width / dpi).toFixed(3) }} </td>
          <td>{{ (whWrapper.height / dpi).toFixed(3) }}</td>
        </tr>
        <tr v-show="px2cmi !== true">
          <td>cm to px</td>
          <td>{{ Math.round((whWrapper.width / inchToCm) * dpi) }}</td>
          <td>{{ Math.round((whWrapper.height / inchToCm) * dpi) }}</td>
        </tr>
        <tr v-show="px2cmi !== true">
          <td>inch to px</td>
          <td>{{ Math.round((whWrapper.width) * dpi) }} </td>
          <td>{{ Math.round((whWrapper.height) * dpi) }}</td>
        </tr>
      </tbody>
    </table>
</template>

<script>
export default {
  props: ["px2cmi", "whWrapper", "dpi", "inchToCm"]
}
</script>