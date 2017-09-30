<template>
    <div id="add-report" class="container">
        <h3 class="text-muted">Add Report</h3>
        <form>
            <div class="form-group">
                <label for="title">Report Title:</label>
                <input id="title" type="text" class="form-control" v-model="report.title" required>
            </div>
            <div class="form-group">
                <label for="accomplishments">Accomplishments:</label>
                <input id="accomplishments" type="text" class="form-control" required>
            </div>
            <div class="form-group">
                <label for="risks">Risks:</label>
                <input id="risks" type="text" class="form-control" required>
            </div>
            <div class="form-group">
                <label for="issues">Issues:</label>
                <input id="issues" type="text" class="form-control" required>
            </div>
        </form>
        <div id="preview">
            <h3 class="text-muted">Preview Report</h3>
            <p class="lead">Title: {{report.title}} </p>
            <ul>
                <li v-for="(item, index) in report.accomplishments">{{item.item}} <button class="btn btn-danger btn-sm" v-on:click="removeItem(index)">X</button></li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            report: {
                title: "",
                accomplishments: [
                    { item: "Lorem ninja ipsum dolor sit amet" },
                    { item: "consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt" },
                    { item: "Ut ninja wisi enim ad minim veniam, quis nostrud" },
                    { item: "Duis ninja autem vel eum iriure dolor in hendrerit" }
                ]
            }

        }
    },
    methods:{
        removeItem: function(index){
            console.log(index);
            this.report.accomplishments.splice(index,1);            
        }
    }
}
</script>

<style scoped>

</style>


