<template>
    <div class='ui basic content center aligned segment'>
        <button class='ui basic button icon' v-on:click="toggleForm">
            <i v-show='!isCreating' class='plus icon'></i>
            <i v-show='isCreating' class='minus icon'></i>
        </button>
        <div class='ui centered card' v-show="isCreating">
            <div class='content'>
                <div class='ui form'>
                    <div class='field'>
                        <label>Title</label>
                        <input type='text' v-model="titleText" ref='title' defaultValue=''>
                    </div>
                    <div class='field'>
                        <label>Project</label>
                        <input type='text' v-model="projectText" ref='project' defaultValue=''>
                    </div>
                    <div class='ui buttons'>
                        <button class='ui blue button' v-on:click="sendForm">
                            Create
                        </button>
                        <button class='ui red button' v-on:click="toggleForm">
                            Cancel
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            titleText: '',
            projectText: '',
            isCreating: false,
        }
    },
    methods:{
        toggleForm(){
            this.isCreating = !this.isCreating
        },
        sendForm(){
            if (this.titleText.length > 0  && this.projectText.length >0){
                const title = this.titleText
                const project = this.projectText
                this.$emit('create-todo',{
                    title,
                    project,
                    done: false,
                })
                this.titleText = ''
                this.projectText = ''
            }
            this.toggleForm()
        }
    }
}
</script>