<template>
  <header>
    <div class="logo">Boolflix</div>
    
    <div class="search">
        <form action="get">
            <input type="search" name="" id="search">
            <button type="submit">Cerca</button>
        </form>
    </div>
  </header>
</template>

<script>
export default {
    name: "MyHeader"
}
</script>

<style lang="scss">
    @import "../style/generalStyle.scss";
    header{
        width: 100%;
        height: 100px;
        background-color: $bg-color-second;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 40px;
        .logo{
            font-weight: bold;
            font-size: 50px;
            color: $primary-color;
            text-transform: uppercase;
        }
        #search{
            height: 50px;
            width: 200px;
            background-color: $bg-color-first;
            border: none;
            border-radius: 10px;
            margin-right: 10px;
            color: white;
            font-size: 20px;
            padding: 10px;
        }
        button{
            height: 50px;
            width: 60px;
            color: white;
            background-color: $primary-color;
            border: none;
            border-radius: 10px;
        }
    }
</style>