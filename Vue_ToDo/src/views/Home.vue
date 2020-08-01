<template>
  <div>
    <p class="text">Welcome to my ToDo app made on Vue JS</p>
    <p class="text">This is my first Vue JS Project.</p>

    <div class="card">
      <router-link to="/todos">
      <img src="https://cdn.pixabay.com/photo/2016/10/23/17/06/calendar-1763587_960_720.png" alt="Loading...">
        <p class="pi">👾👾👾👾👾👾👾👾👾👾👾👾👾</p>
        <p class="pi">👾👾👾👾👾👾👾👾👾👾👾👾👾</p>
        <p class="pi">👾👾👾\_Check it out!_/👾👾👾</p>
        <p class="pi">👾👾👾👾👾👾👾👾👾👾👾👾👾</p>
        <p class="pi">👾👾👾👾👾👾👾👾👾👾👾👾👾</p>


      </router-link>
    </div>

  </div>
</template>

<style lang="less">
  * {
    text-decoration: none;
    font-family: "Ubuntu Mono";
  }
  .text {
    font-size: 300%;

    font-weight: bold;
  }
  img {
    width: 100%;
  }
  .card {
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    transition: 0.3s;
    width: 20%;

    position: relative;
    margin: 0 auto;
  }

  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
  }

</style>