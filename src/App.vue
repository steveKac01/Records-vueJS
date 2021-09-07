<template>
  <div id="app">
    <nav class="navbar navbar-expand-md navbar-dark fixed-top bg-dark">
      <a class="navbar-brand" href="#">Disco U V2.0</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarCollapse" aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarCollapse">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Link</a>
          </li>

        </ul>
      </div>
    </nav>
    <main role="main" class="fluid-container m-4">
        <div class='row'>

            <div class="col-8">

                <div class="card mb-3" >
                  <div class="row no-gutters">
                    <div class="col-m-4 m-2">
                      <img height='150px' src="https://media.pitchfork.com/photos/5d7a863e0db1d10008f20007/master/w_1600%2Cc_limit/FKA-twigs-Two-Weeks.jpeg" alt="...">
                    </div>
                    <div class="col-md-8">
                      <div class="card-body">
                        <h5 class="card-title">Artist</h5>
                        <p class="card-text">Album</p>
                        <p class="card-text"><small class="text-muted">Note</small></p>

                      </div>
                    </div>
                  </div>
                  <div class="card-footer bg-dark">
                      <small class="text-white">5 en Stock </small>
                  </div>
                </div>


            </div>
            <div class="col-4">
                <div class="card bg-light mb-3" style="max-width: 18rem;">
                  <div class="card-header">Infos & Filters</div>
                  <div class="card-body">
                    <h5 class="card-title">Sort </h5>
                    <p class="card-text">Some sorting options</p>
                    <h5 class="card-title">Filter</h5>

                  </div>
                </div>
            </div>


        </div>


    </main>

  </div>
</template>

<script>


export default {
  name: 'App',
  components: {},
}
</script>

<style lang="scss">
  @import "./assets/navbar-top-fixed.css";
  @import "../node_modules/bootstrap/scss/bootstrap.scss";
</style>
