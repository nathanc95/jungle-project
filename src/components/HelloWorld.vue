<template>
  <div class="container">
    <!-- Title -->
    <div class="row">
      <h1 style="text-align: center;color: white;">The Jungle FastRider Service</h1>
    </div>
    <!--End title -->

    <!-- explanation -->
    <div class="row" style="margin-top: 25px;">
      <div class="col-md-4">
          <img src="../assets/ico-g-01.png"
               alt="ticket"
               class="img-circle"
               style="background-color:#373737;">
        <p>
          Enter your park ticket #pin number,
          then select the desired ride
          while nothing the stated return time
        </p>
      </div>
      <div class="col-md-4">
        <img src="../assets/ico-g-02.png"
             alt="ticket"
             class="img-circle"
             style="background-color:#373737;">
        <p>
         Press 'submit' to confirm and retrieve your access code
        </p>
      </div>
      <div class="col-md-4">
        <img src="../assets/ico-g-03.png"
             alt="ticket"
             class="img-circle"
             style="background-color:#373737;">
        <p>
          When the time comes,
          use the special FastRider line to cut out a considerable,
          wait time.
        </p>
      </div>
    </div>
    <!-- end Explanation -->

    <!-- Input form -->
    <div class="row" style="margin-top: 25px;">
      <div class="form-group">
        <div class="col-md-10">
          <input type="text" class="form-control">
        </div>
        <div class="col-md-2">
          <button class="btn"
                  style="background-color:#4c4c4b">
            <span style="color: white;">
              submit
            </span>
          </button>
        </div>
      </div>
    </div>
<!-- End Input Form -->

  </div>
</template>

<script>
export default {
  name: '',
  data () {
    return {
      msg: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
