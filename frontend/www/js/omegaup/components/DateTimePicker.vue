<template>
  <input class="form-control"
        size="16"
        type="text">
</template>

<script>
import {T} from '../omegaup.js';
export default {
  props: {
    value: Date,
    format: {
      type: String,
      'default': 'mm/dd/yyyy hh:ii',
    },
  },
  data: function() { return {};},
  watch: {
    value: function(val) { $(this.$el)
                               .data('datetimepicker')
                               .setDate(val);},
  },
  mounted: function() {
    var self = this;
    $(self.$el)
        .datetimepicker({
          format: self.format,
          defaultDate: self.value,
          language: T.locale,
        })
        .change(function(e) {
          self.$emit('input', $(self.$el).data('datetimepicker').getDate());
        });
    $(this.$el).data('datetimepicker').setDate(this.value);
  },
};
</script>
