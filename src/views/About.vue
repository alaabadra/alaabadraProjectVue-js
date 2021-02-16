<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col-sm-9 mx-auto">
        <h4 class="col-sm-12 mx-auto text-center hw">
          Send verificaion
        </h4>
        <div class="col-sm-12 row mx-auto p-0 mt-3">
          <i
            class="fas fa-mobile fa-3x mx-auto p-3"
            style="color: #663399;
             background-color: rgba(145, 61, 136, .2); 
             border-radius: 40px;
             height: 80px;
             width: 80px"
          ></i>
        </div>
        <p class="col-sm-12 text-center hw p-0 mt-5">
          Verify Your Mobile
        </p>
        <p class="col-sm-12 text-center p-0">
          The mobile number we currently have for you is:
          <strong>(555)555-555</strong>
        </p>
        <div class="col-sm-12 p-0" style="border-bottom: 1px solid grey"></div>
        <p class="col-sm-12 mx-auto text-center mt-3 lw">
          To continue, you must be holding your mobile device and be prepaired
          to recieve text messagen once verified, you will not be able to change
          your mobile number on file easily
        </p>
        <div class="col-sm-8 mx-auto row">
          <!-- <div class="col-sm-12 mx-auto bg-light rounded-lg purple--text text-center hw">
            3335
          </div> -->
          <!-- <span class="col-sm-5 mx-auto mt-3 badge btn-purple badge-pill hw btn">
            Resend NOW
          </span> -->
          <button
            class="col-sm-9 mx-auto mt-3 btn-fill-purple rounded-pill hw btn mb-5"
          >
            SEND TEXT
          </button>
          <p class="col-sm-12 mx-auto text-center mt-3">
            Not your correct mobile?
            <strong>
              <a href="" style="color: black">Enter a new mobile here</a>
            </strong>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.purple--text {
  color: #663399;
}
.hw {
  font-weight: 700;
}
.btn-purple {
  color: #663399;
  border: 1px solid #663399;
}
.btn-purple:hover {
  color: white;
  border: 1px solid #663399;
  background-color: #663399;
}
.btn-fill-purple {
  color: white;
  background-color: #663399;
}
.btn-fill-purple:hover {
  color: #663399;
  border: 1px solid #663399;
  background-color: white;
}
</style>
