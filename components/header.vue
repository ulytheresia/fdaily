<template>
  <nav class="navbar header" role="navigation" aria-label="main navigation">
    <div class="container">
      <div class="navbar-brand">
        <a role="button" class="navbar-burger burger" aria-label="menu">
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
        <a class="navbar-item">
          <img src="~assets/ini.png" />
        </a>
      </div>

      <div class="navbar-menu">
        <!-- menu -->
        <div class="navbar-start">
          <b-input
            expanded
            placeholder="Search..."
            type="search"
            icon="magnify"
            icon-clickable
            @icon-click="searchIconClick"
          >
          </b-input>
        </div>
        <!-- end -->
        <div class="navbar-end">
          <div class="buttons">
            <b-button type="is-primary" icon-left="account"
              >LOGIN/SIGNUP</b-button
            >
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
