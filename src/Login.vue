<template>
  <div className="login">
    <h4 style="margin-top:30px;margin-bottom:30px">Logging in ...</h4>
  </div>
</template>

<script>
export default {
  name: "Login",
  mounted() {
    let name = this.$route.query.name;
    let email = this.$route.query.email;
    let idToken = this.$route.query.id_token;
    let accessToken = this.$route.query.access_token;

    let payload = {
      name: name,
      email: email,
      idToken: idToken,
      accessToken: accessToken
    }

    if (name && email && idToken && name != '' && email != '' && idToken != '') {
      this.$store.commit("login", payload);
      this.$store.dispatch("checkPartner");
    } else {
      this.$store.commit("logout");
    }

    this.$router.push("/");
  }
};
</script>

<style scoped>
</style>