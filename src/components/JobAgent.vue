<template>

    <div>
        <div class="website-name">
            <p class="website-name__main">job<span class="website-name__secondary">Agent</span></p>
            <img class="profile_picture" :src="`/assets/img/profile_pic.png`" alt="photo">
        </div>
        <p class="job-search_header">Job Search</p>
        <div class="job-search">
            <div class="search-container">
                
                <i class="fa fa-search fa-lg" aria-hidden="true"></i>
                <input type="text" v-model="search" placeholder="Search" class="search-bar"/>
            </div>
            
            <div class="filter-box">
                <img class="filter" :src="`/assets/img/filter.svg`" alt="filter">
            </div>
            <!-- <button class="filter-box" @click="sortBy('views')"></button> -->
        </div>
        
        <div class="job-sort">
            <p style="font-weight: bold;">Sort by:</p>
            <p>Views<img class="arrow" :src="`/assets/img/arrow.svg`" alt="filter"></p>
                          
        </div>

        <div v-for="job in filteredJobs" :key="job.name" class="job">
            <div class="company-logo">
                <img :src="`/assets/img/${job.company}.png`" alt="logo">
            </div>
            
            <div class="company-data">
                <p class="title">{{job.name}}</p>
                <div class="comp_loc">
                    <span>Company:</span>
                    <span class="comp_loc__value">{{job.company}}</span>
                </div>
                <div class="comp_loc">
                    <span class="comp_loc">Location:</span>
                    <span class="comp_loc__value">{{job.location.city}}, {{job.location.country}}</span>
                </div>
                <div class="date_view">
                    <div class="date_view__section">
                        <img :src="`/assets/img/time.svg`" alt="time">
                        <span class="post_date">Posted {{job.postedDaysAgo}} days ago</span>
                    </div>
                    <span class="dot"></span>
                    <div class="date_view__section">
                        <img :src="`/assets/img/eye.svg`" alt="eye">
                        <span class="views">{{job.views}} Views</span>
                    </div>
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
    import jobData from "../source/jobs-mock.json"

    export default {
        data(){
            return{
                jobs: jobData.jobs,
                search: '',
                sort: false,
            }
        },

        name: 'JobAgent',
        
        computed: {
            
            filteredJobs: function() {
                
                return this.sortBy('views').filter((job)=>{
                    return job.name.toLowerCase().includes(this.search.toLowerCase())
                });
            }
        },

        
        methods: {
            sortBy(prop) {
                // console.log(prop)
                // console.log(this.filteredJobs)
                return this.jobs.sort((a,b) => a[prop] < b[prop] ? 1 : -1)
            }
        },
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    div {
        margin: 16px auto;
        max-width: 350px;
        max-height: 150px;
    }

    .website-name {
        display: flex;
        justify-content: flex-end;
        margin: 16px auto;
        max-width: 350px;
        align-items: center;
        text-align: center;
    }

    .website-name__main {
        font-weight: 900;
        font-size: 20px;
        line-height: 20px;
        /* identical to box height, or 100% */

        text-align: center;
        letter-spacing: -0.24px;

        color: #EEAB02;
        margin-right: 95px;
    }

    .website-name__secondary {
        font-style: italic;
        font-weight: 300;
        font-size: 20px;
        line-height: 20px;
        /* identical to box height, or 100% */

        text-align: center;
        letter-spacing: -0.24px;

        color: #000000;
    }

    .job-search {
        margin: 0 auto;
        max-width: 350px;
        display: flex;
        justify-content: space-between;
        height: 60px;
    }

    .search-container {
        width: 90%;
    }

    i {
        position: absolute;
        padding: 15px 10px;
    }


    input[type=text]{
        font-family: Roboto;
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 16px;

        color: #636363;
    }

    .job-search_header {
        margin: 0 auto;
        font-weight: bold;
        font-size: 16px;
        line-height: 19px;
        text-transform: uppercase;
    }

    .search-bar {
        background: #EAEAEA;
        border-radius: 8px;
        height: 40px;
        width: 87%;
        border: none;
        
        padding: 0 0 0 30px;
    }

    .filter-box {
        width: 40px;
        height: 40px;
        background: #FFC803;
        border-radius: 8px;
        position: relative;
        // background-image: "/assets/img/filter.svg";
        // align-items: center;
        // text-align: center;
    }

    .filter {
        position: absolute;
        margin: auto;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        height: 18px;
    }

    .job-sort {
        margin: 0 auto;
        max-width: 350px;
        display: flex;
        justify-content: space-between;
        font-size: 14px;
    }

    .arrow {
        margin-left: 10px;
    }

    .job {
        display:flex;
        background: #FFFFFF;
        box-shadow: 0px 4px 8px rgba(33, 33, 33, 0.16);
        border-radius: 8px;
        margin: 16px auto;
        max-width: 350px;

    }

    .company-data {
        margin: 0px;
        width: 100%;
    }

    .title {
                
        font-weight: bold;
        font-size: 12px;
        line-height: 14px;
        text-transform: uppercase;
        margin: 16px 16px 8px 0;
        padding-right: 70px;
    }

    .company-logo {
        margin: 16px 16px 82px 16px;
               
    }
    
    .comp_loc {
        display: flex;
        justify-content: space-between;
        margin: 0 16px 4px 0;
        // width: 262px;
    }

    .comp_loc__value {
        text-align: right;
        text-decoration-line: underline;

        color: #E06D06;
 
    }

    .date_view {
        
        display: flex;
        margin: 10px 28px 16px 0;
        align-items: center;
        text-align: center;
        
    }
    
    .date_view__section {
        
        display: flex;
        justify-content: space-between;
    }

    .date_view__section img {
        margin-right: 8px;
    }

    .dot {
        width: 4px;
        height: 4px;
        border-radius: 30px;
        background: #C4C4C4;
        text-align: center;
        align-content: center;
        margin-left: 10px;
        margin-right: 16px;
    }

</style>
