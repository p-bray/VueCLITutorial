<template>
    <section>
        <h2>
            Here's your current bookings:
        </h2>
        <div class="row" v-for="(booking, index) in bookings" :key="index">
            <div>{{ booking.name }}</div>
        </div>
        <div class="row">Total: {{ totalDisplay() }}</div>
    </section>
</template>

<script>

export default {
    name: 'BookingList',
    props: {
        bookings: Array
    },
    computed: {
        totalDisplay() {
            let totalCost = 0;
            if (this.bookings && bookings.length > 0){
                totalCost = 
                    //array.map creates a new array with a function or other operation 
                    //called on each element in the array. 
                    //here, we create a new array that contains all the prices of the bookings. 
                    this.bookings.map(b => b.price) 
                        //array.reduce returns a single value consisting of the results of 
                        //all the elements in the array having a operation performed on them. 
                        //here, a is the accumulator value (the value resulting from the last call of the callback funtion)
                        //b is the current value in the array. 
                        .reduce((a,b) => a+b);
            }
            return '$ ' + totalCost.toLocaleString('en-US');   
        }
    }
};


</script>


<style scoped>
</style>