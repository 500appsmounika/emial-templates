<template>
<div class="aign-item-center justify-between w-full h-full">
    <div class="mt-2">
      <input type="email" 
      v-model="formdata.name"
      name="email"
       id="email" 
      class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6" 
      placeholder="Enter email" />
    </div>
 
    
    <div class="mt-2">
      <input type="email"
      v-model="formdata.subject"
       name="email" 
       id="email" 
       class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        placeholder="subject" />
    </div>

  
    <div class="mt-2">
      <textarea rows="4" 
      v-model="formdata.body"
      name="comment" 
      id="comment" 
      class="block w-full rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:py-1.5 sm:text-sm sm:leading-6" />
    </div>
  
  </div>
  <button type="button" 
  class="rounded-full bg-white px-2.5 py-1 text-xs font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50">Cancel</button>
  <button type="button" 
  @click="postData()"
  class="rounded-full bg-indigo-600 px-2.5 py-1 text-xs font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Add</button>
</template>
<script setup>

const emit=defineEmits(["post-data"])
let postData=()=>{

let tamplateData={
    name:props.formdata.name,
    subject:props.formdata.subject,
    body:props.formdata.body 
}
emit('post-data',tamplateData)
}
const props=defineProps({
  open:Boolean,
    formdata:Object,
    default:()=>[]
})


</script>