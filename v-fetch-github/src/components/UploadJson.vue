<template>
    <form @submit.prevent="uploadJson">
        <label for="location">location:</label>
        <input type="text" required v-model="cityLocation">
        <label for="location">time:</label>
        <input type="text" required v-model="cityTime" placeholder="07:15 pm">
        <label for="location">temperature:</label>
        <input type="number" required v-model="cityTemp">
        <label for="location">City abbreviation: </label>
        <input type="text" required v-model="cityAbbr" placeholder="NY">
        <button type="submit">Add city</button>
    </form>
    <div>
        <p>location: {{cityLocation}}</p>
        <p>time: {{cityTime}}</p>
        <p>temperature: {{cityTemp}} degrees</p>
        <p>Abbr: {{cityAbbr}}</p>
    </div>
</template>
<script>
    export default {
        data () {
            return {
                cityLocation: '',
                cityTime: '',
                cityTemp: '',
                cityAbbr: ''
            }

        },
        methods: {
            uploadJson () {
                const jsonData = {
                    location: this.cityLocation,
                    abbr: this.cityAbbr,
                    time: this.cityTime,
                    temperature: this.cityTemp
                }
                fetch("https://musaubrian.github.io/host-js/data/weather.json", {
                    method: 'PUT',
                    headers: {
                        'Access-Control-Allow-Origin':'http://127.0.0.1:5173/',
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(jsonData)
                })
                .then((Response) => Response.json())
                .then(jsonData => {
                    console.log("Success:", jsonData);
                })
                .catch((error) => {
                    console.error("Error: ", error);
                });
            }
        }
    }
</script>
<style>
    form {
        display: flex;
        flex-direction: column;
        flex-wrap: nowrap;
        justify-content: center;
        align-items: center;
        padding: 1rem;
        width: 90%;
        font-weight: 90%;
        background-color: blanchedalmond;
        border-radius: 15px;
    }
    input {
        width: 70%;
        border: none;
        border-bottom: 2px solid #000;
        background-color: transparent;
        padding: 0.5rem;
        font-size: 1.2rem;
    }
</style>