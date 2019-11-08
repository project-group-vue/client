<template>
  <div class="col" style="border-right: 1px solid whitesmoke; background-color: white;">
                    <div class="addtodo" style="justify-content: center; margin: 15px 50px 5px 2px;">
                        <div class="namecontent" style="text-align: left;;color: rgb(2, 101, 250); font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">
                            <h5>Add New Stories</h5>
                        </div>
                        <div class="field">
                            <p class="control has-icons-left has-icons-right">
                                <input class="input" type="text" placeholder="Title" id="title-todo">
                                <span class="icon is-small is-left">
                                <i class="fas fa-envelope"></i>
                              </span>
                                <span class="icon is-small is-right">
                                <i class="fas fa-check"></i>
                              </span>
                            </p>
                        </div>
                        <div class="field">
                            <div class="control">
                                <textarea class="textarea" placeholder="Descrition" id="description-todo"></textarea>
                            </div>
                        </div>
                        <div class="field">
                            <p class="control">
                                <button class="button is-link is-light" style="color: rgb(53, 49, 48);" id="addtodo-button">
                                
                              </button>
                            </p>
                        </div>
                        <div class="button-group">

                        </div>
                        <div class="list-project">
                            <ul id="project-list">
                                
                            </ul>
                        </div>
                    </div>
                </div>
</template>

<script>
export default {

}
</script>

<style>
body {
    background-color: aliceblue;
}
</style>