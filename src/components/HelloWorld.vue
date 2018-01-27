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
        <div style="padding-left: 50%;">
          <img src="../assets/ico-g-01.png"
               alt="ticket"
               class="img-circle"
               style="background-color:#373737;">
        </div>
        <p>
          Enter your park ticket #pin number,
          then select the desired ride
          while nothing the stated return time
        </p>
      </div>
      <div class="col-md-4">
        <div style="padding-left: 50%">
        <img src="../assets/ico-g-02.png"
             alt="ticket"
             class="img-circle"
             style="background-color:#373737;">
        </div>
        <p>
         Press 'submit' to confirm and retrieve your access code
        </p>
      </div>
      <div class="col-md-4">
        <div style="padding-left: 50%">
        <img src="../assets/ico-g-03.png"
             alt="ticket"
             class="img-circle"
             style="background-color:#373737;">
        </div>
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
          <input type="text"
                 class="form-control"
                 placeholder="#pin"
                 v-model="postBody"
                 @change="postPost()">
          <ul v-if="errors && errors.length">
            <li v-for="error in errors">
              {{error.message}}
            </li>
          </ul>
        </div>
        <div class="col-md-2">
          <button class="btn"
                  style="background-color:#4c4c4b;"
          >
            <span style="color: white;">
              submit
            </span>
          </button>
        </div>
      </div>
    </div>
<!-- End Input Form -->

    <!-- products -->
    <div class="row" style="">
      <div class="col-md-2"
           style="background-color:#373737;margin-left: 15px;margin-top: 15px;"
           v-for="result in results"
           @click="attachRed =! attachRed"
           :class="{active:attachRed}"
           >

       <div class="row"
            style="height:3px;"
            v-bind:style="myStyle">
       </div>
        <div class="row">
          <span class="float-right" style="float: right;">{{result.zone.name}}</span>
        </div>
        <div class="row">
          <p style="color:white;font-size: medium;">{{result.name}}</p>
        </div>
        <div class="row">
          <img src="../assets/ico-g-03.png"
               alt="ticket"
               class="img-circle"
               style="background-color:#373737;"
               height="30" width="30">
          <span style="padding-right: 50px;">{{result.return_time}}</span>
          <img src="../assets/ico-g-01.png"
               alt="ticket"
               class="img-circle"
               style="background-color:#373737"
               height="30" width="30">
          <span style="">{{result.remaining_tickets}}</span>
        </div>
      </div>
    </div>
    <!-- end Products -->

  </div>
</template>

<script>
  import axios from 'axios'
export default {
  data () {
    return {
      attachRed:false,
      results:[],
      postBody:'',
      errors:[]
    }
  },
  methods:{

    postPost(){
      axios.post('http://localhost:3000/api/tickets',{
        access_code:this.postBody
      })
        .then(response =>{})
        .catch(e =>{
          this.error.push(e)
        })
    },

  },
  created(){
    axios.get('http://localhost:3000/api/rides')
      .then(response => {
        this.results = response.data

      })
      .catch(e => {
        this.error.push(e)
      })
   }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
p{
  text-align: center;
}
  span{
    color:#656565;
  }

  .active{
    border:1px solid red;
  }


</style>
