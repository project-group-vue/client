<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-primary">
        <a class="navbar-brand" href="#">EDYIBPITSM</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
            <li class="nav-item active">
                <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="#">Link</a>
            </li>
            <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                Dropdown
                </a>
                <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                </div>
            </li>
            <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
            </li>
            </ul>
            <form class="form-inline my-2 my-lg-0">
            <button class="btn btn-outline-danger my-2 my-sm-0" type="submit" @click.prevent="logout">Logout</button>
            </form>
        </div>
    </nav>
  </div>
</template>

<script>
export default {
    methods: {
        logout() {
                Swal.fire({
                title: "GoodByee...",
                imageUrl: 'http://giphygifs.s3.amazonaws.com/media/mNEoEM3WP57KU/giphy.gif',
                imageHeight: 350,
                imageAlt: 'A tall image',
                showConfirmButton: false,
                timer: 2000,
                icon: 'success',
                })
        }
    }
}
</script>

<style scoped>
.navbar {
    background-color: black !important;
}

.navbar-brand {
    color: yellow !important;
}
</style>>

