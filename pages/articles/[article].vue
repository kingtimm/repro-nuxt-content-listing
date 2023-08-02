<template>
  <main>
    <ContentDoc v-slot="{ doc }">
      Published at: {{ doc.publishedAt }}
    </ContentDoc>
    <ContentDoc></ContentDoc>
  </main>
</template>
