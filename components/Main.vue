<template>
  <div
    class="grid grid-rows-3 grid-flow-col grid-cols-4 border w-[80vw] mx-auto my-5 rounded-lg pr-[4px]"
  >
    <div
      class="row-span-3 bg-gray-50 border-r p-5 rounded-l-lg h-[calc(100vh-150px)] overflow-auto"
    >
      <button
        type="button"
        class="rounded bg-indigo-50 px-2 py-1 text-sm font-semibold text-indigo-600 shadow-sm hover:bg-indigo-100"
      >
        Add Template
      </button>
      <section>
        <List :TemplateData="TemplateData"></List>
        <p>{{ data1 }}</p>
      </section>

      <Edit></Edit>
    </div>
    <div>
      <Add @post-data="postData" :formdata="formdata"></Add>
    </div>
  </div>
</template>
<script setup>
const data1 = ref();
const formdata = {
  name: "",
  subject: "",
  body: "",
};
//get
let postoptions = {
  method: "GET",
  headers: {
    "Content-Type": "application/json",
    Accept: "application/json",
    Authorization:
      "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiZDI1NjgxM2E2NjdjNDExM2ExZDBiNDY2NGI4YmRhNzUiLCJkIjoiMTY4MDA3OCIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzY5MTR9.ESaiQVZYh45IyIJaP4A3YZO73FRLxd_lW1ATays2dhM",
  },
};
const { data: templateData } = await useAuthLazyFetch(
  "https://v1-orm-lib.mars.hipso.cc/email-templates/?offset=0&limit=100&sort_column=id&sort_direction=desc"
);

//post
const postData = async (tamplateData) => {
  console.log("ok", tamplateData);
  let postoptions = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
      Authorization:
        "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYmZlOTY3MDc0YzJhNGVlNDhiODFlYWU1ZmU5ZThhMjkiLCJkIjoiMTY4MDA4MSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzkyNzB9._HklK6rl9AWu3mp4kRdrOIsxyEP-jNpG7kgF3K-5GlA",
    },
    body: { tamplateData },
  };
  const { data: addTemplateData } = await useAuthLazyFetchPost(
    "https://v1-orm-lib.mars.hipso.cc/api/email-templates/",
    postoptions
  );
  templateData.value.unshift(form);
  formsData.value = {};
};
</script>
