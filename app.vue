<script setup lang="ts">
// import { AppDataSource } from './server/database'
import { Example } from '~/server/database/entities/Example'

const insertExample = async () => {
  const exampleData = {
    description: 'blah',
    details: 'blub',
  }

  // Will throw `DataSource is not set for this entity.` error when executed
  const example = new Example()
  await example.update(exampleData) // internally calls `.save()`

  // // Will throw `DataSource is not set for this entity.` error when executed
  // await Example.save<Example>(exampleData)

  // // Will throw `connection.driver.options is undefined` error on page load
  // await AppDataSource.manager.save(Example, exampleData)

  // // Will throw `connection.driver.options is undefined` error on page load
  // const exampleRepository = AppDataSource.getRepository(Example)
  // await exampleRepository.save(exampleData)
}
</script>

<template>
  <div class="h-screen w-full bg-white dark:bg-gray-800 dark:text-gray-100">
    <Head>
      <Title>sidebase</Title>
    </Head>
    <div class="grid place-content-center h-screen w-screen">
      <a-button @click="insertExample">
        Insert Example Entity
      </a-button>
    </div>
  </div>
</template>
