<template>
    <div class="toast-wrapper">
        <div class="toast">
            Veuillez entrer une valeur
        </div>
    </div>
</template>

<style>

.toast-wrapper {
    position: fixed;
    width: 100%;
    top: 20px;
    z-index: 1;
}

.toast {
    padding: 20px;
    color: white;
    background: #ff0062;
    border-radius: 10px;
    box-shadow: 1px 3px 5px rgba(0, 0, 0, 0.2);
    max-width: 400px;
    margin: 0 auto;
    font-weight: bold;
}

</style>