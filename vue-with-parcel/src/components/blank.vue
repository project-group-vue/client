<template>
    <div>
    <div class="card mb-3">
                <img :src="image" class="card-img-top" alt="" height="300" width="200">
                <div class="card-body">
                      <div class="custom-file">
                        <input type="file" class="custom-file-input" id="validatedCustomFile" required>
                        <label class="custom-file-label" for="validatedCustomFile">Choose file...</label>
                        <div class="invalid-feedback">Example invalid custom file feedback</div>
                    </div>
                    <hr>
                     <button type="button" class="btn btn-primary">Primary</button>
                    <button type="button" class="btn btn-secondary">Secondary</button>
                    <button type="button" class="btn btn-success">Success</button>
                </div>
    </div>
        <div class="line"></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            image: 'https://www.google.com/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&uact=8&ved=2ahUKEwiLlaSx59jlAhVTjeYKHQc1DBEQjRx6BAgBEAQ&url=https%3A%2F%2Fwww.shutterstock.com%2Fvideo%2Fclip-1286998-laptop-blank-white-screen&psig=AOvVaw1gMO0BA3P7wOQ3TP_Squ3O&ust=1573240406612953'
        }
    }
}
</script>

<style>

</style>