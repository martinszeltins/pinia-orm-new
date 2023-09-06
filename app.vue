<template>
  <div>
    {{ users }}
  </div>

  <div>
    <button @click="addUser">
        Add user
    </button>
  </div>
</template>

<script setup lang="ts">
    import User from './stores/models/user'
    import { useRepo } from 'pinia-orm'

    const userRepo = useRepo(User)

    // Getting all users
    const users = userRepo.all()

    const addUser = () => {
        userRepo.insert({
            name: 'John Doe',
            email: 'john@doe.com'
        })
    }
</script>
