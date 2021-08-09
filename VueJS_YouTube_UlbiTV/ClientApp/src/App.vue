<template>
    <div class="app">
        <form @submit.prevent>
            <h4>Сщздание поста</h4>
            <input v-bind:value="title" 
                   @input="title=$event.target.value"
                   class="input"
                   type="text"
                   placeholder="Название" />
            <input v-bind:value="body"
                   @input="body=$event.target.value"
                   class="input"
                   type="text"
                   placeholder="Описание" />
            <button class="btn"
                    v-on:click="crPost">
                Создать
            </button>
        </form>
        <div class="post" v-for="post in posts" :key="post.id">
            <div><strong>Название поста: </strong>{{post.title}}</div>
            <div><strong>Описание Поста:</strong>{{post.body}}</div>
        </div>
       
    </div>
</template>

<script>
    export default {
        data() {
            return {
                posts: [
                    { id: 1, title: 'JavaScript', body: 'JavaScript универсальный язык' },
                    { id: 2, title: 'JavaScript 2', body: 'JavaScript универсальный язык 2' },
                    { id: 3, title: 'JavaScript 3', body: 'JavaScript универсальный язык 3' },

                ],
                title: '',
                body: ''

            }
        },
        method:{
            crPost(){
                const newPost = {
                    id: Date.now(),
                    title: this.title,
                    body: this.body,
                }
                this.posts.push(newPost);
            }
        }
    }
   
</script>

<style>
    *{
        margin:0;
        padding:0;
        box-sizing:content-box;

    }
    .app{
        padding:15px;
    }
    .post{
        padding:15px;
        border:3px solid teal;
        margin-top:15px;
    }
    form{
        display:flex;
        flex-direction:column;
    }
    .input{
        width:98%;
        border:2px solid teal;
        padding:10px 15px;
        margin-top:15px;
    }
    .btn{
        margin-top:15px;
        align-self:flex-end;
        padding:10px 15px;
        background:none;
        color:teal;
        border:2px solid teal;

    }
</style>
