<template>
  <!-- Responsive calendar - START -->
  <div class="responsive-calendar col-lg-6">
    <div class="controls">
      <a class="pull-left" data-go="prev"
        ><div class="btn btn-primary">Prev</div></a
      >
      <h4><span data-head-year></span> <span data-head-month></span></h4>
      <a class="pull-right" data-go="next"
        ><div class="btn btn-primary">Next</div></a
      >
    </div>
    <hr />
    <div class="day-headers">
      <div class="day header">Mon</div>
      <div class="day header">Tue</div>
      <div class="day header">Wed</div>
      <div class="day header">Thu</div>
      <div class="day header">Fri</div>
      <div class="day header">Sat</div>
      <div class="day header">Sun</div>
    </div>
    <div class="days" data-group="days"></div>
  </div>
  <!-- Responsive calendar - END -->
</template>

<script type="text/javascript">
const date = new Date()
const year = date.getFullYear()
const month = date.getMonth() + 1
$(document).ready(function () {
  $(".responsive-calendar").responsiveCalendar({
    //time: "2013-05",
    time: `${year}-${month}`,
    events: {}
  })
})
</script>

<style type="text/css">
.responsive-calendar {
  padding-bottom: 40px;
}
</style>
