<template>
    <div>
        <h3 class="text-danger text-justified">Administrator</h3>
        <div class="table-responsive">
        <table class=" col-md-10 table table-inverse">
            <thead class="thead-inverse">
                <tr class="danger">
                    <td>Name</td>
                    <td>Sex</td>
                    <td>Birthday</td>
                    <td>Email</td>
                    <td>Phone Number</td>
                    <td>Company</td>
                    <td>Official Visit</td>
                    <td>Escort Name</td>
                    <!-- <td>Actions</td> -->
                </tr>
            </thead>

            <tbody>
                <tr class="active" v-for="user in users">
                    <td>{{ user.name }}</td>
                    <td>{{ user.sex }}</td>
                    <td>{{ (new Date(user.birth)).toLocaleDateString('en-US') }}</td>
                    <td>{{ user.email }}</td>
                    <td>{{ user.telephone }}</td>
                    <td>{{ user.company }}</td>
                    <td>{{ user.visit }}</td>
                    <td>{{ user.esc_name }}</td>
                    <!-- <td><router-link :to="{name: 'EditUser', params: { id: user._id }}" class="btn btn-primary">Edit</router-link></td>
                    <td><button class="btn btn-danger" v-on:click="deleteItem(user._id)">Delete</button></td> -->
                </tr>
            </tbody>
        </table>
        </div>
    </div>
</template>

<script>

    export default {
        data(){
            return{
                users: []
            }
        },

        created: function()
        {
            this.fetchItems();
        },

        methods: {
            fetchItems()
            {
              let uri = 'http://localhost:4000/users';
              this.axios.get(uri).then((response) => {
                  this.users = response.data;
              });
            },
            deleteItem(id)
            {
              let uri = 'http://localhost:4000/users/delete/'+id;
              this.users.splice(id, 1);
              this.axios.get(uri);
            }
        }
    }
</script>
