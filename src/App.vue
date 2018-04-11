<template>
  <div id="application">
    <SiteHeader/>

    <div class="row columns">
      <h1 class="contrast">Social snapshot</h1>
      <p>
        Save a snapshot of a component for social media.
      </p>
    </div>
    <div class="row">
      <div class="columns medium-8">
        <form @submit.prevent="download">

          <label for="line1">Line 1</label>
          <input
            v-model="form.line1"
            type="text"
            maxlength="120"
            required>

          <label for="line2">Line 2</label>
          <input
            v-model="form.line2"
            type="text"
            maxlength="120">

          <label for="icon">Icon</label>
          <select v-model="form.icon">
            <option value="">None</option>
            <option value="exclamation">
              <i class="fa fa-exclamation"/>
              Exclamation
            </option>
            <option value="bell">
              <i class="fa fa-bell"/>
              Bell
            </option>
          </select>

          <button type="submit">Download</button>
        </form>
      </div>
      <div class="columns medium-16">
        <SiteWideAlert
          ref="siteWideAlert"
          v-bind="form"/>
      </div>
    </div>
  </div>
</template>

<script>
import domtoimage from 'dom-to-image'
import FileSaver from 'file-saver'
import SiteHeader from './components/SiteHeader'
import SiteWideAlert from './components/SiteWideAlert'

export default {
  components: {
    SiteHeader,
    SiteWideAlert
  },
  data () {
    return {
      form: {
        line1: 'Due to extremely cold conditions, the City is implementing special measures to keep homeless people safe.',
        line2: 'In effect: 11:30 a.m. on Wednesday, Feb. 22 to 11:30 a.m. on Saturday, Feb. 25',
        icon: 'exclamation'
      }
    }
  },
  methods: {
    download () {
      const el = this.$refs.siteWideAlert.$el
      domtoimage.toBlob(el).then((blob) => {
        FileSaver.saveAs(blob, 'site-wide-alert.png')
      })
    }
  }
}
</script>

<style lang="sass">
$fa-font-path: "~font-awesome/fonts"
@import "~font-awesome/scss/font-awesome"
@import '~phila-standards/src/sass/phila-app'
</style>
