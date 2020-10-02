<template>
    <div class="progress">
      <div class="progress-bar bg-info" role="progressbar" :style="{ width : progress + '%'}" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
        {{productListLength}}/10
      </div>
    </div>
</template>

<script>
import { eventBus } from '../main'
  export default {
    data() {
        return {
            progress: 0,
            productListLength: 0
        }
    },
    created() {
      eventBus.$on("productListUpdated", (length) => {
        this.productListLength = length
        this.progress = length * 10
      })
    },
  }
</script>

