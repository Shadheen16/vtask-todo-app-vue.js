<template>
 <div >
    <button @click="onClick()" class=" transform text-white font-extrabold text-xs sm:text-base rounded cursor-pointer px-1 sm:my-1 bg-black bg-opacity-60 shadow-sm hover:text-white hover:scale-110 hover:bg-yellow-600 py-1">{{ text }}</button>
 </div>  
</template>

<script>

export default{
    name:'Button',
    props: {
        text: String,
    },
    methods: {
        onClick(){
            this.$emit("toggle-add-task")
        }
    }
}
</script>