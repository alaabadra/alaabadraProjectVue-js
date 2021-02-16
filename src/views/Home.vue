<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col-sm-9 mx-auto">
        <h4 class="col-sm-12 mx-auto text-center hw">
          Verify Email
        </h4>
        <div class="col-sm-12 row mx-auto p-0 mt-3">
           <i
            class="fas fa-envelope-open-text fa-3x mx-auto p-3"
            style="color: #663399;
             background-color: rgba(145, 61, 136, .2); 
             border-radius: 40px;
             height: 80px;
             width: 80px"
          ></i>
        </div>
        <p class="col-sm-12 text-center p-0 mt-5 hw">
          A verification email has been sent
        </p>
        <p class="p-2">
          <span class="lw"> Please click on the link in the email sent to </span
          ><strong>example@example.com</strong>
        </p>
        <div class="col-sm-12 p-0" style="border-bottom: 1px solid grey"></div>
        <p class="col-sm-12 mx-auto text-center mt-3 lw">
          For improved security , your verification link will expired other 6
          hours . If it has expired , you will be directed to this page where
          you can resend email
        </p>
        <div class="col-sm-8 mx-auto row">
          <input
            class="col-sm-12 mx-auto bg-light
             form-control purple--text text-center 
             rounded-lg
             "
            value="3335"
            style="font-size: 1.5rem; letter-spacing: 10px;"
          />
          <button
            class="col-sm-5 mx-auto mt-3  btn-purple rounded-pill  btn mb-3"
          >
            RESEND NOW
          </button>
          <button
            class="col-sm-5 mx-auto mt-3  btn-fill-purple rounded-pill  btn mb-3"
          >
            SUBMIT CODE
          </button>
          <p class="col-sm-12 mx-auto text-center mt-3">
            <span class="lw"> Not your correct address?</span>
            <strong>
              <a href="" style="color: black">Update your email address</a>
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
.lw {
  font-size: 1rem !important;
  font-weight: 100 !important;
}
.hw {
  font-weight: 700 !important;
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
  color: purple;
  border: 1px solid #663399;
  background-color: white;
}
</style>
