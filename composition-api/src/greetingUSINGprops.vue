<template>
    <div>
        <h3>
            using props - {{firstName}} {{LastName}}
        </h3>
        <h3>
            using computed(options) -{{ fullName }}
        </h3>
        <h3>
            using computed(composition) - {{ FullName }}
        </h3>
    </div>
    <button @click="sendEvent">Call Heroes</button>
</template>

<script>
import { computed } from 'vue'

    export default {
        name: 'greetingUSINGprops',

        props: ['firstName', 'LastName'],


        // If we need to get hold of the component props when using the composition API 
        // it is available as the first argument at the setup method.
        setup(props, context){
            const FullName = computed(() => {
                return `${props.firstName} ${props.LastName}`
            })

            // sending a custom event from a child component to a parent component.
            function sendEvent(){
                context.emit("callHero", FullName.value)
            }

            return{
                FullName,
                sendEvent
            }
        },

        computed: {
            fullName(){
                return `${this.firstName} ${this.LastName}`
            }
        }
    }
</script>


<style scoped>

</style>