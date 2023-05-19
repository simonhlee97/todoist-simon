<script setup>

</script>

<template>
  <nav>
    <ul class="nav-left">
      <li><i class="fa-solid fa-bars"></i></li>
      <li><i class="fa-solid fa-house"></i></li>
      <li><i class="search-icon fa-solid fa-magnifying-glass"></i><input type="text" placeholder="검색" class="search-field" /></li>
    </ul>

    <ul class="nav-right">
      <li><i class="fa-solid fa-plus"></i></li>
      <li><i class="fa-solid fa-chart-line"></i></li>
      <li>0/5</li>
      <li><i class="fa-regular fa-circle-question"></i></li>
      <li><i class="fa-regular fa-bell"></i></li>
      <li><i class="fa-solid fa-circle"></i></li>
    </ul>
  </nav>
</template>

<style lang="less" scoped>
  nav {
    background-color: var(--todoist-orange);
    display: flex;
    position: sticky;
    top: 0px;
    justify-content: space-between;
    padding: 6px 22px;
    z-index: 90;
  }
  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    align-items: center;
    display: flex;
  }
  nav ul li {
    display: inline;
    color: rgba(255, 255, 255, 0.877);
    margin: 0 8px;
    font-size: 12pt;
    font-weight: 200;
    cursor: pointer;
  }
  input {
    width: 202px;
    border: none;
    border-radius: 3px;
    background: var(--light-orange);
    padding: 3px 6px 3px 26px;
    font-size: 10pt;
  }
  
  .search-icon {
    position: absolute;
    padding: 5px;
    min-width: 40px;
  }
  .search-field {
    color: white;
  }
  .avatar {
    height: 15px;
    width: 15px;
    border-radius: 50%;
    background-color: grey;
  }
</style>