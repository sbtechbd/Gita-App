<script>
import axios from 'axios';

export default {
  name: 'App',
  mounted() {
    axios.get('https://bhagavad-gita3.p.rapidapi.com/v2/chapters/', {
      headers: {
        'X-RapidAPI-Key': '1993953dc4mshd75d88b14c0afb8p1ccb21jsn0ae34107db29',
        'X-RapidAPI-Host': 'bhagavad-gita3.p.rapidapi.com'
      }
    })
    .then(response => {
      console.log(response.data);
    })
    .catch(error => {
      console.error('Error fetching data:', error);
    });
  }
};

</script>


<template>
  <div class="min-h-screen bg-gray-100">
    <div class="container py-6">
    <!-- Page Heading -->
    <header class="bg-white shadow">  
      <div class="px-4 py-6 mx-auto max-w-7xl sm:py-8 sm:px-6 lg:px-8">
        <div class="lg:flex lg:items-center lg:justify-start">
          <div class="flex-1 min-w-0">

              <h2 class="text-2xl font-bold leading-9 text-center text-gray-900 sm:text-3xl sm:leading-9 sm:truncate">
                <p>Bhagavadgita App</p>
              </h2>

          </div>
        </div>
      </div>
    </header>
    </div>
    <!-- Page Content -->
    <div class="container py-6">
      <div class="bg-white p-4 shadow rounded">
        <div class="flex -mx-4 items-center mb-6">
          <div class="flex-1 px-4">
            <select class="gita-input" name="" id="">
              <option value="">Select Chapters</option>
            </select>
          </div>

          <div class="flex-1 px-4 text-center">
            <div class="font-bold mb-1 text-lg"> <!-- Corrected spelling from font-blod to font-bold -->
              <p>Chapter Name</p>
            </div>
          </div>

          <div class="flex-1 px-4">
            <select class="gita-input" name="" id="">
              <option value="">Select Verses</option>
            </select>
          </div>
        </div>

          <!-- body Content -->
          <div class="flex-1 px-4"> 
           <p> Lorem ipsum dolor sit amet consectetur adipisicing elit. Saepe itaque dolores commodi recusandae aut odio ducimus explicabo harum ipsa quasi nobis quisquam voluptates consequatur magni iure, nihil quibusdam voluptatibus laudantium? </p>

            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptate eaque dolores itaque inventore voluptatum explicabo vel? Facere mollitia praesentium nostrum, deserunt, repellat numquam voluptas nobis dolorum ullam repudiandae distinctio sed?</p>
          </div>

          
      </div>
    </div>

    <!-- Footer Content -->
    <div class="container py-6">
      <div class="bg-white p-4 shadow rounded text-center"> 
        <p>Footer</p>
    </div>
    </div>
     <!-- End Footer Content -->
  </div> 
  
  
</template>


<style>

</style>
