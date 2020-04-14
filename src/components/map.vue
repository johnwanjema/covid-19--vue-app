<template>
    <div>
        <div>
            <h2>Search and add a pin</h2>
            <label>
                            <gmap-autocomplete
                              @place_changed="setPlace">
                            </gmap-autocomplete>
                            <button @click="addMarker">Add</button>
                          </label>
            <br/>
    
        </div>
        <br>
        <gmap-map :center="center" :zoom="6.8" style="width:100%;  height: 800px;">
            <gmap-marker :key="index" v-for="(m, index) in markers" :position="m.position" @click="infoWindow(m)"></gmap-marker>
        </gmap-map>
    </div>
</template>

<script>
export default {
    name: "GoogleMap",
    data() {
        return {
            // default to Montreal to keep it simple
            // change this to whatever makes sense
            center: {
                lat: 0.355636,
                lng: 37.5833061
            },
            markers: [],
            places: [],
            currentPlace: null
        };
    },

    mounted() {
        this.geolocate();
    },

    methods: {
        infoWindow(m) {
            console.log(m);
            console.log(this.places);
            alert('Nairobi county </br> 100 cases')
        },
        // receives a place object via the autocomplete component
        setPlace(place) {
            this.currentPlace = place;
        },
        addMarker() {
            if (this.currentPlace) {
                const marker = {
                    lat: this.currentPlace.geometry.location.lat(),
                    lng: this.currentPlace.geometry.location.lng()
                };
                this.markers.push({ position: marker,"place":this.currentPlace });
                this.places.push(this.currentPlace);
                // this.center = marker;
                this.currentPlace = null;
            }
        },
        geolocate: function() {
            navigator.geolocation.getCurrentPosition(position => {
                this.center = {
                    lat: position.coords.latitude,
                    lng: position.coords.longitude
                };
            });
        }
    }
};
</script>