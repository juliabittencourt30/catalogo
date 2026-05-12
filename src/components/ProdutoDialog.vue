<script setup>
    import { ref } from 'vue';
    const props = defineProps(['nome', 'preco', 'categoria', 'id'])
    import ButtonChild from './ButtonChild.vue';
    import { formataPreco } from '@/utils/produtoUtils';
    const novopreco = ref(0)
    novopreco.value = props.preco
    defineEmits(['fechar', 'corrigirpreco'])
</script>

<template>
    <div class="overlay">
    <div class="produto-dialog">
        <h2>{{ nome }}</h2>
        <p>Preço: {{ formataPreco(preco) }}</p>
        <p>Categoria: {{ categoria }}</p>
        <input type="number" v-model.number="novopreco" />
        <ButtonChild @clique="$emit('corrigirpreco')">Corrigir Preço</ButtonChild>
        <ButtonChild @clique="$emit('fechar')">Fechar</ButtonChild>
    </div>
    </div>
</template>

<style scoped>
.produto-dialog{
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 24px;
    background-color: white;
    min-width: 320px;
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