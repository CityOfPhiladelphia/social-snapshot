<template>
  <div id="site-wide-alert">
    <div class="row">
      <div class="medium-16 medium-centered">
        <div class="row equal-height pvs">
          <div
            v-if="icon"
            class="small-1 columns center equal icon">
            <div class="valign">
              <div class="valign-cell">
                <i
                  class="fa fa-3x"
                  :class="`fa-${icon}`"
                  aria-hidden="true"/>
              </div>
            </div>
          </div>
          <div class="small-23 columns equal message">
            {{ line1 }}
            <div
              v-if="line2"
              class="dates pts">
              {{ line2 }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    line1: String,
    line2: String,
    icon: String
  }
}
</script>
