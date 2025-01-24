<script setup>
import Card from '@/components/Card.vue';

const cardsData = [
    {
        id: 1,
        bg: "bg-gray-100", 
        title: "For Developers",
        description: "Browse our Vue jobs and start your career today", 
        buttonBg: "bg-black",
        buttonText:"Browse Jobs" 
    },
    {
        id: 2,
        bg: "bg-green-100",
        title: "For Employers",
        description: "List your job to find the perfect developer for the role", 
        buttonBg: "bg-green-500",
        buttonText: "Add Job",
    }
]

</script>

<template>
    <section class="py-4">
        <div class="container-xl lg:container m-auto">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 p-4 rounded-lg">
                <Card 
                    v-for="data in cardsData"
                    :key="data.id"
                    :bg="data.bg"
                    :title="data.title"
                    :description="data.description"
                    :buttonBg="data.buttonBg"
                    :buttonText="data.buttonText"
                />
            </div>
        </div>
    </section>
</template>