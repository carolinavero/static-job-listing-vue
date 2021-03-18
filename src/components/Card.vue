<template>
    <div class="card-content">
        <div class="card d-flex">
            
            <div class="card-header">

                <div class="img-rounded">
                    <img :src="logo" :alt="company" />
                </div>
                

                <div class="d-flex">
                    <div class="job-title">
                        <h3>{{ company }}</h3>
                    </div>

                    <div v-if="newTag">
                        <span className="new uppercase f-light f-8 p-3-8 br-1 t-center">
                            new
                        </span>
                    </div>
                    <div v-if="featuredTag">
                        <span className="featured uppercase f-light f-8 p-3-8 br-1 t-center">
                            featured
                        </span>
                    </div>

                </div>

                <h2>{{ position }}</h2>

                <div>
                       {{ postedAt }} - {{ contract }} - {{ location }}
                </div>


            </div>

            <div>

                <div className="d-flex f-wrap">

                    <div v-if="languages" >
                        <a href="/" className="tag" v-for="(language, index) in languages" :key="index">
                            {{ language }}
                        </a>
                    </div>

                    <div v-if="tools" >
                        <a href="/" className="tag" v-for="(tool, index) in tools" :key="index">
                            {{ tool }}
                        </a>
                    </div>

                    

                </div>

            </div>

        </div>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: {
        company: {
            type: String,
            required: true
        },
        position: {
            type: String,
            required: true
        },
        logo: {
            type: String,
            required: true
        },
        newTag: {
            type: Boolean,
            required: false
        },
        featuredTag: {
            type: Boolean,
            required: false
        },
        postedAt: {
            type: String,
            required: true
        }, 
        contract: {
            type: String,
            required: true
        }, 
        location: {
            type: String,
            required: true
        },
        languages: {
            type: Array,
            required: false
        },
        tools: {
            type: Array,
            required: false
        }

    }
}
</script>

<style>

.card-content {
    display: flex;
    width: 80%;
}

.img-rounded {
    border-radius: 100px;
    background-color: gray;
    width: 50px;
    height: 50px;
    overflow: hidden;
}

.card {
    background-color: #fff;
    padding: 2rem;
    margin: 1rem;
    border-radius: .5rem;
    box-shadow: 3px 8px 8px #5ba3a429;
    line-height: 1.5;
    width: 100%;

    display: flex;
    align-items: center;
    justify-content: space-between;
}

.card img {
    width: 50px;
    height: auto;
}
h2 {
    font-size: 1rem;
}
h3 {
    font-size: .9rem;
    color: var(--desaturatedDarkCyan);
}
ul {
    list-style: none;
    padding-left: 0;
}
a {
    text-decoration: none;
}

hr {
    margin: 1.5rem 0;
    border: 1px solid #ddd;
}

.tag {
    background-color: var(--lightGrayishCyanBg);
    color: var(--desaturatedDarkCyan);
    font-size: .85rem;
    font-weight: bold;
    padding: 10px;
    border-radius: .5rem;
    margin: 5px;
}


.d-flex {
    display: flex;
}
.f-wrap {
    flex-wrap: wrap;
}
.uppercase {
    text-transform: uppercase;
}
.f-light {
    color: #fff;
}
.t-center {
    text-align: center;
}
.f-8 {
    font-size: .75rem;
}
.p-3-8 {
    padding: .2rem .8rem;
}
.br-1 {
    border-radius: 1rem;
}

.new {
    background-color: var(--desaturatedDarkCyan);
}

.featured {
    background-color: #333;
}

</style>