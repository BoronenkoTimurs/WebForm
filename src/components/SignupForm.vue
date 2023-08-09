<template>
  <form class="max-w-md my-7 mx-auto bg-white p-10 rounded-xl">
    <label class="inline-block tracking-wide text-slate-400 uppercase font-bold"
      >Email:</label
    >
    <input
      class="block mb-2 py-3 outline-none px-2 w-full box-border border-solid border-b-2 border-slate-800 text-slate-600"
      type="email"
      required
      v-model="email"
    />
    <label
      class="inline-block mb-2 tracking-wide text-slate-400 uppercase font-bold"
      >Password:</label
    >
    <input
      class="block py-3 mb-2 outline-none px-2 w-full box-border border-solid border-b-2 border-slate-800 text-slate-600"
      type="password"
      required
      v-model="password"
    />
  </form>
  <p class="text-center">Email: {{ email }}</p>
  <p class="text-center">Password: {{ password }}</p>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
};
</script>
