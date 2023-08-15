<template>
  <form
    @submit.prevent="handleSubmit"
    class="max-w-md my-7 mx-auto bg-white p-10 rounded-xl"
  >
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
    <div class="text-red-400 font-bold" v-if="passwordErr">
      {{ passwordErr }}
    </div>

    <label class="text-slate-400 uppercase font-bold">Role: </label>
    <select
      class="block py-3 mb-2 outline-none px-2 w-full box-border border-solid"
      v-model="role"
    >
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label class="text-slate-400 uppercase font-bold">Skill(alt + ','):</label>
    <input
      class="block py-3 mb-2 outline-none px-2 w-full box-border border-solid border-b-2 border-slate-800 text-slate-600"
      type="text"
      v-model="tempSkill"
      @keyup.alt="addSkill"
    />
    <div
      class="inline-block tracking-wider mt-5 mr-2 px-2 py-2 rounded-2xl bg-slate-300 text-gray-500 font-bold cursor-pointer"
      v-for="skill in skills"
      :key="skill"
    >
      <span @click="removeSkill(skill)">{{ skill }}</span>
    </div>
    <div>
      <input
        v-model="termns"
        class="inline-block w-4 mr-2.5 relative top-0.5"
        type="checkbox"
        required
      />
      <label class="text-slate-400 text-sm uppercase font-mono"
        >Accept terms and conditions!</label
      >
    </div>
    <div class="text-center">
      <button
        class="bg-blue-600 border-none py-3 px-5 mt-5 text-white rounded-3xl"
      >
        Create an Account!
      </button>
    </div>
  </form>
  <p class="text-center">Email: {{ email }}</p>
  <p class="text-center">Password: {{ password }}</p>
  <p class="text-center">Role: {{ role }}</p>
  <p class="text-center">Termns: {{ termns }}</p>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "designer",
      termns: "",
      tempSkill: "",
      skills: [],
      passwordErr: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
          this.tempSkill = "";
        }
        this.tempSkill = "";
      }
    },
    removeSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    handleSubmit() {
      this.passwordErr =
        this.password.length > 5
          ? ""
          : "Small password! Need more than 9 symbols!";
    },
  },
};
</script>
