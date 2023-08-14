<template>
  <header>
    <img src="~/assets/images/negative_logo.png" alt="negative_logo_png" />
    <h1 v-if="isLeaderboardRoute">CLASSIFICAÇÃO</h1>
    <h1 v-else-if="isLoginRoute">LOGIN</h1>
    <h1 v-else-if="isMatchesRoute">PARTIDAS</h1>
    <nav>
      <NuxtLink v-if="isLeaderboardRoute" to="/matches">
        Partidas
      </NuxtLink>
      <NuxtLink v-else to="/leaderboard">
        Classificação
      </NuxtLink>
      <NuxtLink data-testid="header__login_btn" to="/login">
        Login
      </NuxtLink>
    </nav>
  </header>
</template>

<script>
  export default {
  name: 'NuxtHeader',
  computed: {
    isLeaderboardRoute() {
      return this.$route.path === '/leaderboard';
    },
    isLoginRoute() {
      return this.$route.path === '/login';
    },
    isMatchesRoute() {
      return this.$route.path === '/matches';
    }
  }
}
</script>

<style>
  header {
    height: 150px;
    background: #007DF9;
    margin-bottom: 30px;
    padding: 15px;
  }

  header nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  header nav a {
    font-family: 'Inter', 'Courier New', Courier, monospace;
    font-style: normal;
    font-weight: 400;
    font-size: 27px;
    line-height: 33px;
    text-decoration: none;
    color: #000000;
  }

  header nav a:last-of-type {
    display: flex;
    align-items: center;
    flex-flow: column nowrap;
  }
</style>