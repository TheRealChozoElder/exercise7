<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <!-- Part 1 5 Points-->
                    <!-- Create a Signup Form where you retrieve the following Information -->
                    <!-- Full Name (First Name + Last Name) -->
                    <!-- Mail -->
                    <!-- Password -->
                    <!-- Store Data? Yes/No -->
                    <h1>Sign up here!</h1>
                    <hr>
                    <div v-if="customSwitch"
                         class="form-group">
                        <label for="fullName">Full Name</label>
                        <input
                            type="text"
                            id="fullName"
                            class="form-control"
                            v-model.lazy="userData.fullName">
                    </div>
                    <div v-else>
                        <div class="form-group">
                            <label for="firstName">First Name</label>
                            <input
                                type="text"
                                id="firstName"
                                class="form-control"
                                v-model.lazy="userData.firstName">
                        </div>
                        <div class="form-group">
                            <label for="lastName">Last Name</label>
                            <input
                                type="text"
                                id="lastName"
                                class="form-control"
                                v-model.lazy="userData.lastName">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="email">Mail</label>
                        <input
                            type="text"
                            id="email"
                            class="form-control"
                            v-model.lazy="userData.email">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input
                            type="password"
                            id="password"
                            class="form-control"
                            v-model.lazy.trim="userData.password">
                    </div>
                    <div class="form-group">
                        <label for="storeData">Store Data?</label>
                        <br>
                        <label for="yes">
                            <input
                                type="radio"
                                id="yes"
                                value="Yes"
                                class="form-control"
                                v-model="storeData"> Yes
                        </label>
                        &nbsp
                        <label for="no">
                            <input
                                type="radio"
                                id="no"
                                value="No"
                                class="form-control"
                                v-model="storeData"> No
                        </label>
                    </div>
                    <div>
                        <p>Switch between Full Name and First/Last Name inputs</p>
                        <custom-switch v-model="customSwitch"></custom-switch>
                    </div>
                    <div>
                        <br>
                        <button
                            class="btn btn-primary"
                            @click.prevent="submitted">Submit!</button>

                    </div>
                    <!-- Part 2 5 Points -->
                    <!-- Only display the Form if it has NOT been submitted -->
                    <!-- Display the Data Summary ONCE the Form HAS been submitted -->

                    <!-- Part 3 5 Points -->
                    <!-- Edit the Example from above and create a custom "Full Name" Control -->
                    <!-- which still holds the First Name and Last Name Input Field -->
                </div>
            </div>
        </form>
        <hr>
        <div class="row" v-if="isSubmitted"><!-- Part 2 here -->
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p v-if="customSwitch">Full Name: {{ userData.fullName }}</p> <!-- part 3 here -->
                        <p v-else>Full Name: {{ userData.firstName }} {{ userData.lastName }}</p>
                        <p>Mail: {{ userData.email }}</p>
                        <p>Password: {{ userData.password }}</p>
                        <p>Store in Database?: {{ storeData }}</p>
                        <p>Switched: {{ customSwitch }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Switch from './Switch.vue';

    export default {
        data() {
            return{
                userData: {
                    fullName: '',
                    email: '',
                    password: '',
                    firstName: '',
                    lastName: ''
                },
                storeData: '',
                isSubmitted: false,
                customSwitch: true
            }
        },
        components: {
            customSwitch: Switch
        },
        methods: {
            submitted() {
                this.isSubmitted = true;//part 2 also here
            }
        }
    }
</script>

<style>
</style>
