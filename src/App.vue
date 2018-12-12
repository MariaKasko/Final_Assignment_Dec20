<template>
  <div style="padding: 30px;">
    <h1>Final Assignment</h1>

    <h3>1. Display a message</h3>
    <div>{{ message }}</div>

    <h3>2. Add 2 properties</h3>
    {{ value1 }} + {{ value2 }} = {{ value1 + value2 }}

    <h3>3. Display a list</h3>
    <!-- display a list from the myList array in data -->
    <ul>
      <li v-for="item in myList">{{ item }}</li>
    </ul>

    <h3>4. Display a list of lists</h3>
    <!-- display a list of lists from the categorizedList array in data -->
    <ul>
      <li v-for="category in categorizedList">
        {{ category.name }}
        <ul>
          <li v-for="item in category.items">{{ item }}</li>
        </ul>
      </li>
    </ul>

    <h3>5. Display an HTML card using data</h3>
    <!-- use vacationCardData to fill in the below card -->
    <div class="card">
      <div class="card-image">
        <img v-bind:src="vacationCardData.imgSrc" class="img-responsive" />
      </div>
      <div class="card-header">
        <div class="card-title h5">{{ vacationCardData.title }}</div>
        <div class="card-subtitle text-gray">
          {{ vacationCardData.subtitle }}
        </div>
      </div>
      <div class="card-body">{{ vacationCardData.description }}</div>
    </div>

    <h3>6. Display a Card Component</h3>

    <!-- <my-card v-bind="vehichleCardData"></my-card> -->
    <my-card
      v-bind:title="vehichleCardData.title"
      v-bind:subtitle="vehichleCardData.subtitle"
      v-bind:body="vehichleCardData.description"
      v-bind:imgSrc="vehichleCardData.imgSrc"
    ></my-card>

    <h3>7. Display a Card by making a call</h3>
    <!--
      Call and load vehicle-detail.json using axios and display the data in an html card
    -->

    <div class="card">
      <div class="card-image">
        <img v-bind:src="vehicleDetail.imgSrc" class="img-responsive" />
      </div>
      <div class="card-header">
        <div class="card-title h5">
          {{ vehicleDetail.title
          }}<!-- title data -->
        </div>
        <div class="card-subtitle text-gray">{{ vehicleDetail.subtitle }}</div>
      </div>
      <div class="card-body">{{ vehicleDetail.description }}</div>
    </div>

    <h3>8. Display a Card Copmonent by making a call</h3>
    <!--
      Call and load vehicle-detail.json using axios and display the data in a card component
    -->
    <my-card v-bind="vehicleDetail"></my-card>

    <!--
      <my-card
        v-bind:title="vehicleDetail.title"
        v-bind:subtitle="vehicleDetail.subtitle"
        v-bind:body="vehicleDetail.description"
        v-bind:imgSrc="vehicleDetail.imgSrc"
      >
      </my-card>
    -->

    <h3>9. Display a list of cards using data from vehicles-list.json</h3>
    <div>
      <div class="container">
        <div class="columns">
          <div class="column col-4" v-for="vehicle in vehicles">
            <my-card v-bind="vehicle"></my-card>
          </div>
        </div>
      </div>
    </div>

    <h3>10. Display some of Bublbasaur's information from the pokeapi</h3>
    <p>Name:</p>
    <p>Base Experience:</p>
    <p>Weight:</p>

    <h3>11. Display Bulbasaur's abilities in a list from the pokeapi</h3>
    <ul>
      <li>Ability</li>
    </ul>

    <h3>12. Display Bublbasaur's stats in a list from the pokeapi</h3>
    <ul>
      <li>stat name : base_stat</li>
    </ul>

    <h3>13. Display Bublbasaur's first 5 moves in a list from the pokeapi</h3>
    <ul>
      <li>move name</li>
    </ul>

    <h3>
      14. Display Bublbasaur's first 5 moves with power and accuracy in a list
      from the pokeapi
    </h3>
    <ul>
      <li>move name - power - accuracy</li>
    </ul>

    <h3>
      15. BONUS: Display the first 15 pokemon and their first 3 moves (name,
      power, accuracy)
    </h3>
    <ul>
      <li>
        pokemon name
        <ul>
          <li>Move 1</li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
import MyCard from "./components/card";
import axios from "axios";
export default {
  name: "App",
  components: {
    MyCard
  },

  data() {
    return {
      message: "Hello World",
      value1: 1337,
      value2: 42,
      myList: ["Xbox", "Playstation", "Nintendo Switch", "Sega"],
      categorizedList: [
        {
          name: "Category 1",
          items: ["item 1", "item 2", "item 3"]
        },
        {
          name: "Category 2",
          items: ["item a", "item v", "item c"]
        },
        {
          name: "Category 3",
          items: ["item i", "item ii", "item iii"]
        }
      ],
      vacationCardData: {
        title: "My Favorite Vacation",
        subtitle: "Anywhere warmer than here",
        description: "",
        imgSrc:
          "https://media.triseptsolutions.com/sites/VAXWEBWNT/PublishingImages/Themes/Destinations/Aruba_Beach_382x235.jpg"
      },
      vehichleCardData: {
        title: "Toyota Corolla",
        subtitle: "Midsize Sedan",
        description: "Great car that gets you from point a to point b",
        imgSrc:
          "https://postmediadriving.files.wordpress.com/2017/11/chrome-image-395391.png?w=800&h=520&crop=1"
      },
      vehicleDetail: "",
      mytitle: "",
      vehicles: []
    };
  },
  mounted() {
    axios.get("vehicle-detail.json").then(response => {
      this.vehicleDetail = response.data.vehicleDetail;
    });
    axios.get("vehicles-list.json").then(response => {
      this.vehicles = response.data.vehicles;
    });

    // 1. Display the message in data
    // 2. Display the sum of value1 and value 2 in data
    // 3. Display a list from the myList array in data
    // 4. Display a list of lists from the categorizedList array in data
    // 5. Display data from vacationCardData inside the card html provided
    // 6. Build and display a card component by passing vehichleCardData as props to card
    // make sure to create the card component file in components and import it
    // 7. Call and load vehicle-detail.json using axios and display the data in an html card
    // 8. Call and load vehicle-detail.json using axios and display the data in a card component
    // 9. Display a list of cards using data from vehicles-list.json
    // 10. Display some of Bublbasaur's information from the pokeapi
    // get url https://pokeapi.co/api/v2/pokemon/bulbasaur/
    // documentation for the pokeapi can be found: https://pokeapi.co/docs/v2.html/
    // 11. Display Bublbasaur's abilities in a list from the pokeapi
    // 12. Display Bublbasaur's stats in a list from the pokeapi
    // 13. Display Bublbasaur's first 5 movies in a list from the pokeapi
    // 14. Display Bublbasaur's first 5 moves with power and accuracy in a list from the pokeapi
    //   you will have to use https://pokeapi.co/api/v2/move/{name} api to get move details
    //   like power and accuracy, pass the move name to the call, ex:
    //   https://pokeapi.co/api/v2/move/razor-wind
    // 15: BONUS.
    //   a. Display a list of names of the first 15 pokemon from the pokeapi.co api (https://pokeapi.co/api/v2/pokemon/)
    //   b. For each pokeon name in the list, list below their first 3 move name
    //   c. When hovering over each move name display the move accuracy and power
  }
};
</script>
