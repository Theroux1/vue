<script setup>
// import team from "@/team.json";
import TeamHeader from "@/components/Teams/TeamHeader.vue";
import TeamMembers from "@/components/Teams/TeamMembers.vue";
import TeamFooter from "@/components/Teams/TeamFooter.vue";
import {useTeamStore} from "@/stores/TeamStore";
import Modal from "@/components/Modal.vue";
import {ref} from "vue";

let team = useTeamStore();
team.fill();

let showModal = ref(false)
</script>

<template>
  <TeamHeader @add="showModal = true"/>

  <div class="place-self-center flex flex-col gap-y-3" style="width: 725px">
    <TeamMembers/>
  </div>

  <TeamFooter/>

  <Modal :show="showModal" @close="showModal = false">
    <template #header>
      <span></span>
    </template>
    <template #default>
      <p>Add a new team member</p>
      <form class="mt-5">
        <div class="flex">

          <input type="email" placeholder="Enter email address" class="flex-1">
          <button type="submit">Add</button>
        </div>

      </form>
    </template>
  </Modal>
</template>