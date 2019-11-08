<template>
  <div>
    <div class="card mb-3 shadow-sm p-3 mb-5 bg-white rounded">
      <img
        src="https://media.giphy.com/media/ZvjRrOBjxFdWo/giphy.gif"
        class="card-img-top"
        alt
        height="300"
        width="200"
        v-if="!imagePreview"
      />
      <img
        :src="imagePreview"
        class="card-img-top"
        alt
        height="300"
        width="200"
        v-if="imagePreview"
      />
      <div class="card-body">
        <div class="custom-file">
          <!-- <input type="file" class="custom-file-input" id="validatedCustomFile" @change="preview" required>
                        <label class="custom-file-label" for="validatedCustomFile">Choose file...</label>
          <div class="invalid-feedback">Example invalid custom file feedback</div>-->
          <form enctype="multipart/form-data">
            <div class="form-group">
              <label for="exampleFormControlFile1">Example file input</label>
              <input
                type="file"
                class="form-control-file"
                id="file"
                ref="file"
                v-on:change="handleFileUpload"
              />
            </div>
            <input type="submit" @click.prevent="submitFile" v-if="!imagePreview" />
          </form>
        </div>
          <hr v-if="neuralTalk">
          <h4 class="card-title" v-if="neuralTalk">"{{ neuralTalk }}"</h4>
        <hr />
        <div v-if="imagePreview">
          <button type="button" class="btn btn-outline-success" @click="getColorize">Colorize</button>
          <button type="button" class="btn btn-outline-success" @click="getDeepDream">Deep Dream</button>
          <button type="button" class="btn btn-outline-success" @click="getNeuraltalk">Neural Talk</button>
          <button
            type="button"
            class="btn btn-outline-primary"
            @click="publishEvent"
            id="publish"
          >Save Image</button>
        </div>
      </div>
    </div>
    <div class="line"></div>
  </div>
</template>
<script>
import axios from "axios";
export default {
    data() {
        return {
            imagePreview: '',
            image: '',
            baseUrl: 'http://localhost:3000',
            neuralTalk: ''
            
        }
    },
    methods: {

        preview(event) {
            let input = event.target
            if (input.files && input.files[0]) {
                let reader = new FileReader()
                reader.onload = (e) => {
                    this.image = e.target.result
                }
                reader.readAsDataURL(input.files[0])
            }
            
        },

        getColorize() {
            Swal.showLoading()
            axios({
                url : `${this.baseUrl}/image/colorize`,
                method: 'POST',
                headers : {
                    token: localStorage.getItem('token')
                },
                data: {
                    imageUrl: this.imagePreview
                }
            })
            .then(({data}) => {
                Swal.close()
                this.imagePreview = data
            })
            .catch((err) => {
                    Swal.close()
                    Swal.fire({
                    icon: 'error',
                    title: 'Oops...',
                    text: `${err.response.data.message}`
                    })
            })
                
        },
        getDeepDream () {
            Swal.showLoading()
            axios ({
                url: `${this.baseUrl}/image/deepdream`,
                headers: {
                    token: localStorage.getItem('token')
                },
                data: {
                    imageUrl: this.imagePreview
                },
                method: 'POST'
            })
            .then (({data}) => {
                Swal.close()
                this.data
            })
            .catch ((err) => {
                console.log(err.response.data)
                Swal.close()
                Swal.fire({
                icon: 'error',
                title: 'Oops...',
                text: `${err.response.data.message}`
                })
            })
        },
        getNeuraltalk () {
            Swal.showLoading()
            axios({
                url: `${this.baseUrl}/image/neuraltalk`,
                headers: {
                    token: localStorage.getItem('token')
                },
                data: {
                    imageUrl: this.imagePreview
                },
                method: "POST"
            })
            .then(({data})=> {
                  Swal.close()
                this.neuralTalk = data
            })
            .catch ((err) => {
                Swal.close()
                Swal.fire({
                icon: 'error',
                title: 'Oops...',
                text: `${err.response.data.message}`
                })
            })
        },
        sendFile() {
            axios({
                url: `${this.baseUrl}/image/share`,
                headers: localStorage.getItem('token'),
                data: {
                    image: this.image
                }
            })
            .then (({data}) => {
                Swal.fire({
                position: 'top-end',
                icon: 'success',
                title: 'Your pictures has been saved',
                showConfirmButton: false,
                timer: 1500
                })
            })

        },

    handleFileUpload() {
      this.image = this.$refs.file.files[0];
    },
    submitFile() {
      let formData = new FormData();
      console.log(formData);

      formData.append("image", this.image);
      Swal.showLoading();
      axios({
        method: "post",
        url: "http://localhost:3000/image/uploadgcs",
        data: formData,
        headers: {
          token: localStorage.getItem("token")
        },
        config: {
          headers: {
            "Content-Type": "multipart/form-data"
          }
        }
      })
        .then(({ data }) => {
          console.log(data, "Dari then");
          Swal.close();
          this.imagePreview = data.data.location;
        })
        .catch(err => {
          console.log(err);

          Swal.close();
          console.log(err.response.data);
        });
    },

    publishEvent() {
      axios({
        method: "POST",
        url: `${this.baseUrl}/image/share`,
        data: {
          image: this.imagePreview
        },
        headers: {
          token: localStorage.getItem("token")
        }
      }).then(response => {
        Swal.fire({
          icon: "success",
          title: "Success",
          text: "Saved to Public"
        });

        this.$emit("fetchingData");
      });
    }
  }
};
</script>
<style>
#publish {
  margin-left: 70px;
}
</style>