<template>
    <section>
        <h2>Book now!</h2>
        <form>
            <div class="row">
                <label for="cruise-cabin">Select class:</label>
                <!-- here we use v-bind to make it so that cabinIndex is updated in the method. -->
                <select id="cruise-cabin" v-model="cabinIndex">
                    <!-- if you hit submit with no option selected, nothing should happen. -->
                    <option disabled value="-1">Select a cabin please.</option>
                    <!-- display the options. cabin will be a prop that is passed in during instantiation. -->
                    <option v-for="(cabin, index) in cabins" :value="index" :key="index">
                        {{ cabin.name }} $ {{ cabin.price.toLocaleString('en-US') }}
                    </option>
                </select>
            </div>
            <div class="row">
                <button class="button" @click="bookCabin" type="button">Book!</button>
            </div>
        </form>
    </section>
</template>

<script>
export default {
    name: "BookingForm",
    //will be called in the bookCabin to alert parent component that the booking was created. 
    emits: ['bookingCreated'],
    methods: {
        //called when user hits submit on form
        bookCabin(){
            if(this.cabinIndex < 0) return;
            console.log(this.cabinIndex);
            this.$emit('bookingCreated', this.cabinIndex);
            this.cabinIndex = -1;
        },
    },
    //array of cabins to display
    props: {
        cabins: Array,
    },
    //cabinIndex for iteration through cabinArray. Exposing it for the view. 
    //we set this to -1 to signify that there has not been a cabin selected yet. 
    data() {
        return { 
            cabinIndex: -1 
        }
    }
}
</script>

