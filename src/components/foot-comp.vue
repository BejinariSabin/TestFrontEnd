<template>
  <div class="footerClass ">
      <h6 class="footerName">Created by: {{yourName}} </h6>
      <p class="assist"> Internship 2022 </p>  
  </div>
</template>

<script>
export default {
    name:"FooterComponent",
    data() {
        return {
            yourName: "Bejinari Sabin-Mihai",
        }
    },
    
    
}
</script>

<style>
.footerClass{
   height: 40px;
   background-color: #ededed;
   color: #515356; 
   display: inline-flex;
   flex-direction: row;
   align-items: center;
   align-content: center;
   justify-content: space-between;
   width:100% !important;
}
.assist{
   justify-content: flex-end;
}
.footerName{
    justify-content: flex-start;
}
</style>