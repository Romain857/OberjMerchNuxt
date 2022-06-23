<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="secondary">
    <b-navbar-brand href="/">OberjMerch</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">

        <b-nav-item-dropdown text="Team" right>
          <b-dropdown-item href="#">Gabriel</b-dropdown-item>
          <b-dropdown-item href="#">Romain</b-dropdown-item>
          <b-dropdown-item href="#">Antoine</b-dropdown-item>
          <b-dropdown-item href="#">Yohann</b-dropdown-item>
        </b-nav-item-dropdown>

      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
  </div>
</template>

<style>
    #title{
        text-align:center;
    }
</style>
