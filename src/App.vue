<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <h1>File a Complaint</h1>
                    <hr>
                    <div class="form-group">
                        <label for="email">Mail</label>
                        <input
                                class="form-control"
                                id="email"
                                type="text"
                                v-model.trim="userData.email">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input
                                :value="userData.password"
                                @input="userData.password = $event.target.value"
                                class="form-control"
                                id="password"
                                type="password">
                    </div>
                    <div class="form-group">
                        <label for="age">Age</label>
                        <input
                                class="form-control"
                                id="age"
                                type="number"
                                v-model.number="userData.age">
                    </div>

                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                    <label for="message">Message</label><br>
                    <!-- Interpolation between <textarea>{{ test }}</textarea> doesn't work!-->
                    <textarea
                            class="form-control"
                            id="message"
                            rows="5"
                            v-model="message"/>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <div class="form-group">
                        <label for="sendmail">
                            <input
                                    id="sendmail"
                                    type="checkbox"
                                    v-model="sendMail"
                                    value="SendMail"> Send Mail
                        </label>
                        <label for="sendInfomail">
                            <input
                                    id="sendInfomail"
                                    type="checkbox"
                                    v-model="sendMail"
                                    value="SendInfoMail"> Send Infomail
                        </label>
                    </div>

                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                    <label for="male">
                        <input
                                id="male"
                                type="radio"
                                v-model="gender"
                                value="Male"> Male
                    </label>
                    <label for="female">
                        <input
                                id="female"
                                type="radio"
                                v-model="gender"
                                value="Female"> Female
                    </label>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 from-group">
                    <label for="priority">Priority</label>
                    <select
                            class="form-control"
                            id="priority"
                            v-model="selectedPriority">
                        <option v-for="priority in priorities">{{ priority }}
                        </option>
                    </select>
                </div>
            </div>
            <hr>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <app-switch v-model="dataSwitch"/>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <button @click.prevent="submitForm"
                            class="btn btn-primary">Submit!
                    </button>
                </div>
            </div>
        </form>
        <hr>
        <div class="row" v-if="isSubmitted">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p>Mail: {{ userData.email }}</p>
                        <p>Password: {{ userData.password }}</p>
                        <p>Age: {{ userData.age }}</p>
                        <p style="white-space: pre">Message: {{ message }}</p>
                        <p><strong>Send Mail?</strong></p>
                        <ul>
                            <li v-for="mail in sendMail">{{ mail }}</li>
                        </ul>
                        <p>Gender: {{ gender }}</p>
                        <p>Priority: {{ selectedPriority }}</p>
                        <p>Switched: {{ dataSwitch }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Switch from './Switch.vue';

    export default {
        
        components: {
            appSwitch: Switch
        },

        data() {
            return {
                userData: {
                    email: '',
                    password: '',
                    age: 21
                },
                message: 'Enter some text',
                sendMail: [],
                gender: 'male',
                priorities: ['High', 'Medium', 'Low'],
                selectedPriority: 'Low',
                dataSwitch: true,
                isSubmitted: false
            }
        },
        
        methods: {
            submitForm() {
                this.isSubmitted = true;
            }
        }
    }
</script>

<style>

</style>
