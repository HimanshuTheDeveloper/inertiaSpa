<template>
    <div>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
            <div class="container-fluid">
                <a class="navbar-brand" href="#">Customers</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent"
                    aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <li class="nav-item">
                            <a class="nav-link active" aria-current="page" href="#">Home</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#">Link</a>
                        </li>
                        <li class="nav-item dropdown">
                            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button"
                                data-bs-toggle="dropdown" aria-expanded="false"> Dropdown </a>
                            <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
                                <li><a class="dropdown-item" href="#">Action</a></li>
                                <li><a class="dropdown-item" href="#">Another action</a></li>
                                <li>
                                    <hr class="dropdown-divider" />
                                </li>
                                <li><a class="dropdown-item" href="#">Something else here</a></li>
                            </ul>
                        </li>
                    </ul>
                    <form class="d-flex">
                        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" />
                        <button class="btn btn-outline-success" type="submit">Search</button>
                    </form>
                </div>
            </div>
        </nav>




<div class="container mt-4 border border-dark">
    <h5 class="text-center">Create Customers</h5>
        <form class="p-3">
            <div class="row">
              <div class="col">
                <input type="text" class="form-control" v-model="name" placeholder="Enter Name">
              </div>
              <div class="col">
                <input type="email"  class="form-control" v-model="email" placeholder="Enter E-Mail">
              </div>
              <div class="col">
                <input type="text" class="form-control" v-model="address" placeholder="Enter Address">
              </div>
              
              <div class="col">
                <button  @click="save()" type="button" class="btn btn-primary form-control">Create</button>
              </div>
            </div>
          </form>
    </div>
    <div class="container mt-4 border border-dark p-2">
    <h4 class="text-center">Customers</h4>
        <div class="container" v-for="customer in customers" :key="customers.name">


            <div class="row">
                <div class="col">
                    <div class="card  d-flex  p-2 " style=" width: 18rem ;">
                        <img src="https://img.pngio.com/customer-customer-png-368_412.png" class="w-25 card-img-top" alt="" style="margin: 0 auto;" />
                        <div class="card-body text-center">
                            <h5 class="card-title">Name - {{ customer.name }}</h5>
                            <p class="card-text">E-mail - {{ customer.email }}</p>
                            <p class="card-text">Address - {{ customer.address }}</p>
                            <p class="card-text">Created At - {{ customer.created_at }}</p>
                            <a  @click="" class="btn btn-primary">Details</a>
                            <!-- <inertia-link :href="$route('customers.show')" class="btn btn-primary">Create User</inertia-link> -->
                        </div>
                    </div>
                </div>
            </div>
        </div>

        </div>
    </div>
</template>

<script>
    export default {
        props: {
            customers: Array,
        },
        data() {
            return {
                name,
                email,
                address
            }
        },
        methods:{
            save : function () {
                console.log(this.name);
                this.$inertia.post('/customers', {
                    name : this.name,
                    email : this.email,
                    address : this.address,
                })
                // this.reset();
                // this.closeModal();
                
            },
        }
    }
</script>