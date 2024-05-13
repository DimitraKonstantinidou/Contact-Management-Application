<template>
    <li>
        <h2>{{ name }} {{ isFavorite ? '(Favorite)' : ''}}</h2>
        <button @click="toggleFavorite">Toggle Favorite</button>        
        <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>        
        <ul v-if="detailsAreVisible">
            <li><strong>Phone:</strong> {{ phoneNumber }}</li>
            <li><strong>Email:</strong> {{ emailAddress }}</li>
        </ul>
        <button @click="deleteFriend">Delete</button>
    </li>
</template>

<script>
export default {
    props: [ 
        'id',
        'name', 
        'phoneNumber', 
        'emailAddress',
        'isFavorite'
    ],
    emits: ['toggle-favorite', 'delete'],
    data() {
        return {
            detailsAreVisible: false,
        }
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFavorite() {
            this.$emit('toggle-favorite', this.id );
        },
        deleteFriend() {
            this.$emit('delete', this.id);
        }
    }
}
</script>