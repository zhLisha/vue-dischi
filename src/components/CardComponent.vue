<template>
<!-- Single Music Card -->
    <div class="card">

        <!-- Album Thumb -->
        <div class="thumb">
            <img :src="cardDetails.poster" :alt="cardDetails.title">
        </div>

        <!-- Album Title -->
        <div class="title">
            <span> {{ cardDetails.title }} </span>
        </div>

        <!-- Album details -->
        <div class="album-details">
            <!-- Artist -->
            <div class="artist-name">
                <span> {{ cardDetails.author }} </span>
            </div>

            <!-- Release's year -->
            <div class="releas-year">
                <span> {{ cardDetails.year }} </span>
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name: 'CardComponent',
    props:{
        cardDetails: Object
    }
}
</script>

<style lang="scss" scoped>
@import '@/style/variables.scss';

.card {
    background-color: $secondColor;
    margin: 10px;
    width: calc((100% / 5) - 20px);
    text-align: center;
    padding: 11px;

    img {
        object-fit: cover;
        overflow: hidden;
        aspect-ratio: 1/1;
    }

    .title {
        color: $mainTextColor;
        text-transform: uppercase;
        padding-top: 15px;
        font-size: 20px;
    }

    .album-details {
        color: $smallTextColor;
        padding-top: 15px;
        font-size: 15px;
        font-weight: 500;
    }
}

</style>