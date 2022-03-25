<template>
  <div class="headerClass ">
    <div class="leftSide">
      <img class="logo" alt="Vue logo" src="../assets/logo.png" style="margin-left:10px"/>
      <b-dropdown  left text="Menu" style="margin-left:10px" variant="primary">
        <b-dropdown-item  href="/">Home</b-dropdown-item>
        <b-dropdown-item  href="/contact">Contact</b-dropdown-item>
        <b-dropdown-item  href="/about-us">About</b-dropdown-item>
      </b-dropdown>
    </div>
    <div class="rightSide">
      <b-icon class="twitterLogo" icon="twitter"></b-icon>
      <b-icon class="facebookLogo" icon="facebook"></b-icon>
      <b-icon class="emailLogo" icon="envelope"></b-icon>
    </div>
  </div>
</template>

<script>
export default {
    name: "HeaderComponent"
};
</script>

<style>
.twitterLogo{
  color: #00a5f3;
  width: 30px;
  height: 30px;
  margin-right: 10px;
}
.facebookLogo{
  color: #3b5596;
  width: 30px;
  height: 30px;
  margin-right: 10px;
}
.emailLogo{
  color: white;
  width: 30px;
  height: 30px;
  margin-right: 10px;
}
.headerClass {
  position: sticky;
  width: 100% !important;
  height: 75px;
  background-color: rgb(0, 0, 0);
  border-bottom: 4px solid #39b2cc;
  color: #444;
  font-size: 16px;
  display: inline-flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}
.leftSide{
  justify-content: flex-start;
}
.rightSide{
  display: flex;
  justify-content: flex-end;
}
.logo {
  width: 50px;
  height: 50px;
}
</style>
