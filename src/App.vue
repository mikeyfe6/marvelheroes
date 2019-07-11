<template>
  <div id="container">
    <div id="app" class="bg-red-700">
      <header>
        <nav>
          <ul>
            <li>
              <router-link to="/">Home</router-link>
            </li>
            <li>
              <router-link to="/about">About</router-link>
            </li>
          </ul>
        </nav>
      </header>

      <router-view />
    </div>
  </div>
</template>

<style lang="scss">
#app {
  text-align: center;
}

nav {
  ul {
    display: flex;
    justify-content: flex-end;
  }

  ul li {
    padding: 1em;
  }

  a {
    font-weight: bold;

    &.router-link-exact-active {
      color: white;
    }
  }
}
</style>
