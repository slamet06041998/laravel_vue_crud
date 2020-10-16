<template>
<div class="container-fluid">
        <div class="btn-group mt-3" role="group" aria-label="Button group with nested dropdown">
            <router-link to="/dashboard" class="btn btn-dark">Dashboard</router-link>
            <router-link to="/user" class="btn btn-dark">User</router-link>
            <router-link to="/barang" class="btn btn-dark">Barang</router-link>
        </div>
            <router-view></router-view>
</div>
</template>