<template>
    <div class="wrapper">
        <h1>Погода в вашем городе</h1>
        <input type="text" placeholder="Введите город...">
        <button>Получить</button>
    </div>
</template>

<script>
export default {

    
}
</script>

<style>
    .wrapper {
        padding: 200px;
        border-radius: 50px;
        box-shadow: 0 0 2px;
    }
    .wrapper h1 {
        margin: 10px 0;
    }
    .wrapper input{
        border: 0;
        background: transparent;
        font-size: 14px;
        border-bottom: 2px solid deepskyblue;
        padding: 5px;
        outline: none;
    }
    .wrapper button {
        border: 0;
        background-color: deepskyblue;
        color: white;
        border-radius: 10px;
        padding: 8px;
        margin: 0 10px;
        transition: transform 0.3s ease;
        cursor: pointer;
    }
    .wrapper button:hover{
        transform: scale(1.1);
    }
</style>
