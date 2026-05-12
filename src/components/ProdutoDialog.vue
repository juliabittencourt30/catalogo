<script setup>
    defineProps(['nome', 'preco', 'categoria', 'id'])
    import ButtonChild from './ButtonChild.vue';
    import { formataPreco } from '@/utils/produtoUtils';
</script>

<template>
    <div class="overlay">
    <div class="produto-dialog">
        <h2>{{ nome }}</h2>
        <p>Preço: {{ formataPreco(preco) }}</p>
        <p>Categoria: {{ categoria }}</p>
        <input type="number" v-model.number="preco" />
        <ButtonChild>Corrigir Preço</ButtonChild>
        <ButtonChild>Fechar</ButtonChild>
    </div>
    </div>
</template>

<style scoped>
.produto-dialog{
    border: 1px solid #ccc;
    padding: 16px;
    margin-top: 16px;
}
.overlay{
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 100;
}
</style>