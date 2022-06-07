<template>
 <div>
   <div class="max-w-sm mt-12 overflow-hidden bg-white rounded shadow-lg">
        
        <div class="px-6 py-4">
          <div class="mb-2 text-xl font-bold text-gray-900">
            {{siteInfo.siteName}}
          </div>
          <p class="text-base text-gray-700">
            {{siteInfo.description}}
          </p>
        </div>
        <div class="px-6 pt-4 pb-2">
          <span
            class="inline-block px-3  mb-2 mr-2 text-sm font-semibold text-gray-700 bg-gray-200 rounded-full"
            ><a>{{siteInfo.facebookUrl}}</a></span
          >
          <span
            class="inline-block px-3  mb-2 mr-2 text-sm font-semibold text-gray-700 bg-gray-200 rounded-full"
            ><a>{{siteInfo.instagramUrl}}</a></span
          >
          <span
            class="inline-block px-3  mb-2 mr-2 text-sm font-semibold text-gray-700 bg-gray-200 rounded-full"
            ><a>{{siteInfo.linkedinUrl}}</a></span
          >
        </div>
      </div>

    <!-- Breadcrumb -->
    <!-- <Breadcrumb breadcrumb="Contact" /> -->
    
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import axios from "axios";

// import Breadcrumb from "../partials/Breadcrumb.vue";
interface User {
  name: string;
  email: string;
  title: string;
  title2: string;
  status: string;
  role: string;
}

const testUser: User = {
  name: "John Doe",
  email: "john@example.com",
  title: "Software Engineer",
  title2: "Web dev",
  status: "Active",
  role: "Owner",
};
const siteInfo = ref([]);
onMounted(async () => {
  await axios
    .get("http://kozmosapi-001-site1.itempurl.com/api/SiteInfo")
    .then((response) => {
      siteInfo.value = response.data;
    });
  console.log(siteInfo);
});
// const deleteItem = async (productId) => {
//   await axios
//   .delete(`http://kozmosapi-001-site1.itempurl.com/api/Products/${productId}`)
//   .then((response) => {
//     let products = [...response.value]
//   })
// }

const users = ref<User[]>([...Array(10).keys()].map(() => testUser));
</script> 


