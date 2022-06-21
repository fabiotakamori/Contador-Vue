<template>
    <div class="box has-text-weight-bold">
        <!--Usamos slot para dizer que tudo que está dentro da div box has .. será renderizado dentro do slot-->
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name:"CompBox"
})
</script>

<style scoped>
.box{
    background-color: #FAF0CA;
}
</style>