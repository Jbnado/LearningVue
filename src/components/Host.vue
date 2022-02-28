<template>
  <section>
    <div class="nav-bar">
      <h1 class="title">Relecloud Galaxy Tours</h1>
      <h2 class="cruise-name">{{ cruise.name }}</h2>
      <div class="cruise-description">{{ cruise.description }}</div>
      <!-- <img
        src=""
        :alt="image.description"
        :style="image.style"
      /> -->
    </div>

    <div>
      <hr />
      <div class="row">
        <div>
          <!-- TODO: Add booking-form -->
          <booking-form
            @bookingCreated="addBooking"
            :cabins="cruise.cabins"
          ></booking-form>
        </div>
        <div>
          <!-- TODO: Add booking-list -->
          <booking-list :bookings="bookings"></booking-list>
        </div>
      </div>
    </div>
    <hr />
    <footer class="row footer">
      <div>
        This favicon was generated using the following graphics from Twitter
        Twemoji: - Graphics Title: 1f9d1-200d-1f680.svg - Graphics Author:
        Copyright 2020 Twitter, Inc and other contributors
        (https://github.com/twitter/twemoji) - Graphics Source:
        https://github.com/twitter/twemoji/blob/master/assets/svg/1f9d1-200d-1f680.svg
        - Graphics License: CC-BY 4.0
        (https://creativecommons.org/licenses/by/4.0/)
      </div>
    </footer>
  </section>
</template>

<script>
import BookingList from "./BookingList.vue";
// TODO: Register next component
import BookingForm from "./BookingForm.vue";
export default {
  name: "HostApp",
  data() {
    return {
      cruise: {
        name: "Cruise to the moon",
        description:
          "Cruise to the moon in our luxurious shuttle. Watch the astronauts working outside the International Space Station.",
        cabins: [
          { name: "Coach", price: 125000 },
          { name: "Business", price: 275000 },
          { name: "First", price: 430000 },
        ],
      },
      bookings: [{ name: "Sample", price: 0 }],
      image: {
        description:
          "An astronaut floats outside the window while you sit in comfort",
        style: { "border-radius": "15px", height: "100%", width: "100%" },
      },
    };
  },

  // TODO: Add components
  components: {
    BookingList,
    // TODO: Add next component
    BookingForm,
  },
  // TODO: Add methods
  methods: {
    addBooking(cabinIndex) {
      const cabin = this.cruise.cabins[cabinIndex];
      const booking = {
        cabin: cabin.name,
        price: cabin.price,
      };
      this.bookings.push(booking);
    },
  },
};
</script>

<style>
body {
  background-color: #f2f2f2;
  font-family: tahoma;
  margin: 0;
}

.title,
.cruise-description,
.cruise-name {
  text-align: center;
  color: white;
  text-shadow: 2px 2px #fff, -1px -1px #fff;
}

@supports (-webkit-text-stroke: 1px #fff) {
  .title,
  .cruise-description,
  .cruise-name {
    color: transparent;
    -webkit-text-stroke: 1px #fff;
    text-shadow: none;
  }
}

.title {
  font-size: 36px;
  top: 50px;
  text-shadow: 2px #000;
}
.cruise-name {
  top: 220px;
}
.cruise-description {
  top: 220px;
}

.row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  vertical-align: middle;
  margin: 2em;
}

.footer {
  margin: 0;
  background: linear-gradient(-50deg, #010801, #0d0d60);
  padding: 6px;
  font-size: 12px;
  background-color: #010801;
  color: #fff;
}

.button {
  background-color: #39495c;
  border-radius: 5px;
  color: white;
  text-align: center;
}

.nav-bar {
  width: 100%;
  height: 500px;
  background: linear-gradient(-50deg, #010801, #0d0d60);
  background-image: url("../assets/cruise.jpg");
  background-size: cover;
  margin-bottom: 25px;
  padding: 6px;
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>