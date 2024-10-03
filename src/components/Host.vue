<script>
import BookingList from './BookingList.vue';
import BookingForm from './BookingForm.vue';
export default {
    name: 'Host',
    data() {
        return {
            cruise: {
                name: 'Cruise to the moon',
                description: 'Cruise to the moon in our luxurious shuttle. Watch the astronauts working outside the International Space Station.',
                cabins: [
                    { name: 'Coach', price: 125000 },
                    { name: 'Business', price: 275000 },
                    { name: 'First', price: 430000 },
                ]
            },
            bookings: [
                { name: 'Sample', price: 0 }
            ]
        }
    },
    components: {
        BookingList,
        BookingForm,
    },
    methods: {
        //You do not have to use a "handle" prefix on event handlers, I just like it. 
        handleBookingCreated(){
            const cabin = this.cruise.cabins[cabinIndex];
            const booking = {
                cabin: cabin.name,
                price: cabin.price
            }
            this.bookings.push(booking);
        }
    }
}
// TODO: Add components

// TODO: Add methods
</script>


<template>
    <div class="nav-bar"></div>
    <h1>Relecloud Galaxy Tours</h1>
    
    <div>
        <h2>{{ cruise.name }}</h2>
        <div>{{ cruise.description }}</div>
        <hr />
        <div>
            <div v-for="(cabin, index) in cruise.cabins" :key="index">
                <div>{{ cabin.name }}</div>
                <div>{{ cabin.price }}</div>
            </div>
        </div>
        <div>
            <BookingList :bookings="bookings"></BookingList>
            <BookingForm :cabins="cruise.cabins" @booking-created="handleBookingCreated"></BookingForm>
        </div>
    </div>
</template>

<style>
body {
    background-color: #f2f2f2;
    margin: 0, 5%;
    font-family: tahoma;
    color: #39495c;
}

.row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    vertical-align: middle;
    margin: 2em;
}

.button {
    background-color: #39495c;
    border-radius: 5px;
    color: white;
    text-align: center;
}

.nav-bar {
    background: linear-gradient(-50deg, #010801, #0d0d60);
    height: 60px;
    margin-bottom: 25px;
}
</style>