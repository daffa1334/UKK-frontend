<template>
  <!-- Sidebar -->
  <ul
    class="navbar-nav bg-gradient-dark sidebar sidebar-dark accordion"
    id="accordionSidebar"
  >
    <!-- Sidebar - Brand -->
    <router-link
      to="/"
      class="sidebar-brand d-flex align-items-center justify-content-center"
      href="index.html"
    >
      <div class="sidebar-brand-icon rotate-n-15">
        <img src="wash.png" class="img-fluid">
      </div>
      <div class="sidebar-brand-text mx-3">WASHWASH</div>
    </router-link>

    <!-- Divider -->
    <hr class="sidebar-divider my-0" />

    <!-- Nav Item - Dashboard -->
    <li class="nav-item">
      <router-link to="/" class="nav-link" href="index.html">
        <i class="fas fa-grip-lines"></i>
        <span>Dashboard</span>
      </router-link>

      <!-- Nav Item - Member -->
    </li>

    <li v-if="isAdmin || isKasir" class="nav-item">
      <router-link to="/member" class="nav-link" href="index.html">
        <i class="fas fa-users"></i>
        <span>Member</span>
      </router-link>
    </li>

    <!-- Nav Item - Outlet -->
    <li v-if="isAdmin" class="nav-item">
      <router-link to="/outlet" class="nav-link" href="index.html">
        <i class="fas fa-store"></i>
        <span>Outlet</span>
      </router-link>
    </li>

    <!-- Nav Item - User -->
    <li v-if="isAdmin" class="nav-item">
      <router-link to="/user" class="nav-link" href="index.html">
        <i class="fas fa-user"></i>
        <span>User</span>
      </router-link>
    </li>

    <!-- Nav Item - Paket -->
    <li v-if="isAdmin" class="nav-item">
      <router-link to="/paket" class="nav-link" href="index.html">
        <i class="fas fa-search"></i>
        <span>Paket</span>
      </router-link>
    </li>

    <!-- Nav Item - Transaksi -->
    <li v-if="isAdmin || isKasir" class="nav-item">
      <router-link to="/transaksi" class="nav-link" href="index.html">
        <i class="fas fa-file-invoice"></i>
        <span>Transaksi</span>
      </router-link>
    </li>

    <li class="nav-item">
      <router-link to="/report" class="nav-link">
        <i class="far fa-file-alt"></i>
        <span>Report</span>
      </router-link>
    </li>
  </ul>
  <!-- End of Sidebar -->
</template>

<script>
export default {
  data() {
    return {
      isAdmin: false,
      isKasir: false,
      isOwner: false,
    };
  },
  created() {
    var user = JSON.parse(this.$store.state.datauser);
    var level = user.level;

    if (level == "admin") this.isAdmin = true;
    else if (level == "kasir") this.isKasir = true;
    else this.isOwner = true;
  },
};
</script>
