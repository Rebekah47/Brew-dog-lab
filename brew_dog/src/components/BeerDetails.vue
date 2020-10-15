<template lang='html'>
    <div v-if="beer">
        <h2>{{beer.name}} </h2>
        <p>Tagline: {{beer.tagline}}</p>
        <p>Description: {{beer.description}}</p>
        <p>First Brewed: {{beer.first_brewed}}</p>
    </div>
</template>

<script>
export default {
    name: "beer-details",
    props: ['beer']

}
</script>

<style>

</style>