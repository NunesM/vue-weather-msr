

<template >


  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 18 ? 'warm' : ''" >
  
    <main>

      <div class="search-box">
        <input 
        type="text"  
        class="search-bar" 
        placeholder="Pesquise a cidade..."
        v-model = "query"
        @keypress = "fetchWeather"
        />
    </div>


        <div class="cards" style="display: flex">
                            
              <div class="card" id="card">
                  <div class="weather-wrap" v-if ="typeof weather.main != 'undefined' " >
                  <div class="container location-box">
                  <div class="location"> {{ weather.name }} , {{ weather.sys.country }}</div><br>
                  <div class="date"> {{ dateBuilder() }}</div>
                  </div>
                  <div class="weather-box">
                  <div class="weather"><img :src="`https://openweathermap.org/img/wn/${weather.weather[0].icon}@2x.png`" alt="weather" /></div>
                  <div class="temp" style="display: flex"> {{ Math.round(weather.main.temp_max)}} °C  <p class = "weather2">{{ Math.round(weather.main.temp_min)}} °C</p></div>
                  </div>
                  </div>
              </div>    
              <div class="card" id="card">
                  <div class="weather-wrap" v-if ="typeof weather.main != 'undefined' " >
                  <div class="container location-box">
                  <div class="location"> {{ weather.name }} , {{ weather.sys.country }}</div> <br>
                  <div class="date"> {{ dateBuilder() }}</div>
                  </div>
                  <div class="weather-box">
                  <div class="weather"><img :src="`https://openweathermap.org/img/wn/${weather.weather[0].icon}@2x.png`" alt="weather" /></div>
                  <div class="temp" style="display: flex"> {{ Math.round(weather.main.temp_max)}} °C  <p class = "weather2">{{ Math.round(weather.main.temp_min)}} °C</p></div>
                  </div>
                  </div>
              </div>  
              <div class="card" id="card">
                  <div class="weather-wrap" v-if ="typeof weather.main != 'undefined' " > 
                  <div class="container location-box">
                  <div class="location"> {{ weather.name }} , {{ weather.sys.country }}</div> <br>
                  <div class="date"> {{ dateBuilder() }}</div>
                  </div>
                  <div class="weather-box">
                  <div class="weather"><img :src="`https://openweathermap.org/img/wn/${weather.weather[0].icon}@2x.png`" alt="weather" /></div>
                  <div class="temp" style="display: flex"> {{ Math.round(weather.main.temp_max)}} °C  <p class = "weather2">{{ Math.round(weather.main.temp_min)}} °C</p></div>
                  </div>
                  </div>
              </div> 
        </div>
      
    </main>

  </div>
</template>

<script>

export default {
    name: "app",
    data() {
        return {
            api_key: "c71b8afcceab845efd129f635d0df5e5",
            url_base: "https://api.openweathermap.org/data/2.5/",
            query: "",
            location: "",
            weather: {}
        };
    }, 
    methods: {
        fetchWeather(e) {
            if ((e.key == "Enter")) {
                fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
                    .then(res => {
                    return res.json();
                }).then(this.setResults);
            } 
        },

        statico(){
          let prov = ["Maputo", "tete", "Nampula", "inhambane"];
         
          function randomNumber(min, max) { 
              return Math.floor(Math.random() * (max - min) + min);
          }

          let s = randomNumber(0, 3);
          this.query = prov[s];

          fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
                    .then(res => {
                    return res.json();
          }).then(this.setResults);
        },

        setResults(results) {
            this.weather = results;
        },

        dateBuilder() {
            let d = new Date();
            let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
            let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
            let day = days[d.getDay()];
            let date = d.getDate();
            let month = months[d.getMonth()];
            let year = d.getFullYear();
            
            return `${day} ${date} ${month} ${year}`;
        }
    },


     
}
  

</script>

<style>
  @import "./assets/css/App.css";
</style>


