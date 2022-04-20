<template>
  <div class="container">
    <br>
    <br>
    <br>
    <br><br><br>
    <div class="row justify-content-left">
      <div class="col-lg-6">
        <div
          class="card o-hidden border-0 border-bottom-dark shadow-lg my-5"
        >
          <div class="card-body bg-dark p-5">
            <div class="text-center">
              <div class="h4 text-white mb-4">Selamat Datang</div>
            </div>
            <form class="user" @submit.prevent="login">
              <div class="form-group">
                <input
                  type="text"
                  class="form-control form-control-user"
                  placeholder="Masukkan username"
                  v-model="account.username"
                />
              </div>
              <div class="form-group">
                <input
                  type="password"
                  class="form-control form-control-user"
                  placeholder="Masukkan password"
                  v-model="account.password"
                />
              </div>
              <button type="submit" class="btn btn-dark btn-user btn-block">
                Login
              </button>
            </form>
          </div>
        </div>
      </div>
      <div class="row justify-content-right"></div>
      <div class="col-lg-6"><img src="laundry.png" class="img" width="550x"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      account: {},
    };
  },
  methods: {
    login() {
      this.axios
        .post("http://localhost/laundry/public/api/login", this.account)
        .then((res) => {
          if (res.data.success) {
            this.$store.commit("setToken", res.data.token);
            this.$store.commit("setUser", JSON.stringify(res.data.user));
            this.$store.commit("setOutlet", JSON.stringify(res.data.outlet));
            this.$router.push("/");
          }
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>
