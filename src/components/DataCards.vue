<template>
    <div class="grid md:grid-cols-2 gap-1">
        <!-- Cases box -->
        <div class="shadow-md bg-blue-200 p-10 m-4 text-center rounded">
            <h3 class="font-bold text-3xl text-metal">Cases</h3>
            <div class="text-2xl mb-4 mt-2">
                <span class="font-bold">New:</span>
                {{newConfirmed}}      
            </div>
            <div class="text-2xl">
                <span class="font-bold">Total:</span>
                {{totalConfirmed}}      
            </div>
        </div>
        <!-- Death box -->
        <div class="shadow-md bg-sky-300 p-10 m-4 text-center rounded">
            <h3 class="font-bold text-3xl text-metal">Deaths</h3>
            <div class="text-2xl mb-4 mt-2">
                <span class="font-bold">New:</span>
                {{newDeaths}}      
            </div>
            <div class="text-2xl">
                <span class="font-bold">Total:</span>
                {{totalDeaths}}      
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'DataCards',
    props: ['newConfirmed', 'totalConfirmed', 'newDeaths', 'totalDeaths']
}
</script>