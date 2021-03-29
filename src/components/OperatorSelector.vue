<template>

<div>
    <button @click="$emit('changeOperator', '+')" class="btn btn-success">Addition <br>(+)</button>
    <button @click="$emit('changeOperator', '-')" class="btn btn-danger">Subtraction <br>(-)</button>
    <button @click="$emit('changeOperator', '/')" class="btn btn-warning">Division <br>(/)</button>
    <button @click="$emit('changeOperator', '*')" class="btn btn-dark">Moltiplication <br>(*)</button>

</div>

  
</template>

<script>
export default {};
</script>

<style>

</style>