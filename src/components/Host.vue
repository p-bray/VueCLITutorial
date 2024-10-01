<script>
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
        <div class="row">
            <div class="" v-for="(cabin, index) in cabins" :key="index">
            </div>
        </div>
    </div>
</template>