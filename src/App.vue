<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      chapters: [],
      currentVerses: [],
      currentContent: [],
    };
  },    
  mounted() {
    // Fetch all chapters
    
    axios.get('https://bhagavad-gita3.p.rapidapi.com/v2/chapters/', {
      headers: {
        'X-RapidAPI-Key': '1993953dc4mshd75d88b14c0afb8p1ccb21jsn0ae34107db29',
        'X-RapidAPI-Host': 'bhagavad-gita3.p.rapidapi.com'
      }
    })
    .then(response => {
      this.chapters = response.data; // Assign response data to the "chapters" data property
    })
    .catch(error => {
      console.error('Error fetching chapters:', error);
    });

    // Fetch current chapter 
    axios.get('https://bhagavad-gita3.p.rapidapi.com/v2/chapters/1/verses/1/', {
      headers: {
        'X-RapidAPI-Key': '1993953dc4mshd75d88b14c0afb8p1ccb21jsn0ae34107db29',
        'X-RapidAPI-Host': 'bhagavad-gita3.p.rapidapi.com'
      }
    })
    .then(response => {
      this.currentVerses = response.data; // Assign response data to the "currentVerses" data property
    })
    .catch(error => {
      console.error('Error fetching current verses:', error);
    });
  }
};


 // Fetch  currentContent body
 axios.get('https://bhagavad-gita3.p.rapidapi.com/v2/chapters/1/verses/1/', {
      headers: {
        'X-RapidAPI-Key': '1993953dc4mshd75d88b14c0afb8p1ccb21jsn0ae34107db29',
        'X-RapidAPI-Host': 'bhagavad-gita3.p.rapidapi.com'
      }
    })
    .then(response => {
      this.currentContent = response.data.description; // Assign response data to the "currentContent" data property
    })
    .catch(error => {
      console.error('Error fetching current verses:', error);
    });
  


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
              <option v-for="chapter in chapters" value=""> {{chapter.name_translated}} - {{chapter.name}}</option>
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
              <option v-for ="verse in currentVerses"  :key="verse" value="">{{currentVerses.verse_number}}</option>
            </select>
          </div>
        </div>

          <!-- body Content Start-->
          <div class="flex-1 px-4"> 
            <div v-if="currentContent.length > 0">
                <div v-for="description in currentContent" :key="description">
                  {{ currentContent.description }}
                </div>
            </div>
            <div v-else>
              <p>Loading...</p>
            </div>
          </div>
           <!-- body Content End-->
          
      </div>
    </div>

    <!-- Footer Content -->
    <div class="container py-6">
      <div class="bg-white p-4 shadow rounded text-center"> 
        <p>Developed by Sbtechbd Technologies</p>
    </div>
    </div>
     <!-- End Footer Content -->
  </div> 
  
  
</template>


<style>

</style>
