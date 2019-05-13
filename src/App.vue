<template>
    <div id="app">
        <main>
            <img src="./assets/burgerQueenLogo.png" alt="Vue.js PWA">
            <br>
            <router-view></router-view>
            <div class="name-counter">
                <div class="form-group">
                    <input type="text" placeholder="¿Cómo te llamas?" v-model="namecounter.name" class="form-control">
                </div>
                <div class="form-group">
                    <input type="number" placeholder="Precio" v-model="namecounter.price" class="form-control">
                </div>
                <div class="form-group">
                    <button @click="add">¿Cuántas hamburguesas quieres?</button>
                </div>
                <div class="form-group">
                    <button @click="saveData" class="btn btn-primary">Confirmar</button>
                </div>
                <p> Hola {{ namecounter.name }}, quieres {{ namecounter.counter }} hamburguesas de ${{ namecounter.price }}.</p>
            </div>
        </main>
    </div>
</template>

<script>
import { fb, db } from '../firebase'
export default {
    name: 'app',
    data() {
        return {
            namecounter: {
                counter: 0,
                name: null,
                price: null,
            }
        };
    },
    methods: {
        add() {
            this.namecounter.counter += 1;
        },
        saveData() {
            db.collection("namecounter").add(this.namecounter)
                .then(function(docRef) {
                    console.log("Document written with ID: ", docRef.id);
                })
                .catch(function(error) {
                    console.error("Error adding document: ", error);
                });
            test.firestore.js

        },
    },
};
</script>

<style>
body {
    margin: 0;
}

#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
}

main {
    text-align: center;
    margin-top: 40px;
}

header {
    margin: 0;
    height: 56px;
    padding: 0 16px 0 24px;
    background-color: #35495E;
    color: #ffffff;
}

header span {
    display: block;
    position: relative;
    font-size: 20px;
    line-height: 1;
    letter-spacing: .02em;
    font-weight: 400;
    box-sizing: border-box;
    padding-top: 16px;
}
</style>
