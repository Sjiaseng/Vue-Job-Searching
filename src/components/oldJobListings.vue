<script setup>
import jobData from '@/jobs.json';
import { ref, defineProps } from 'vue';
import JobListing from '@/components/JobListing.vue';
import { RouterLink } from 'vue-router';

defineProps({
    limit: Number,
    showButton: {
        type: Boolean,
        default: false
    }
})

const jobs = ref(jobData);  // -- stored as value (jobs.json)
console.log(jobs);
// const jobs = ref(jobData.jobs); -- stored in object (jobs2.json)
</script>

<template>
    <section class="bg-blue-50 px-4 py-10">
        <div class="container-xl lg:container m-auto">

            <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
                Browse Jobs
            </h2>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">

                <JobListing v-for="job in jobs.slice(0, limit || jobs.length)" :key="job.id" :job="job">
                    {{ job.title }} 
                </JobListing>

            </div>

        </div>

        <br>
        <br>
        <section v-if="showButton" class="m-auto max-w-lg my-5 px-6">
            <RouterLink to="/jobs" class="block bg-black text-white text-center py-4 px-6 rounded-xl giverLbg-gray-700">
                View All Jobs
            </RouterLink>
        </section>

    </section>

</template>