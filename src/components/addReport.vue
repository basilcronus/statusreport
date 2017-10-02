<template>
    <div id="add-report" class="container">
        <h3 class="text-muted">Add Report</h3>
        <form>
            <div class="form-group">
                <label for="title">Report Title:</label>
                <input id="title" type="text" class="form-control" v-model.lazy="report.title" required>
            </div>
            <div class="form-group">
                <label for="accomplishments">Accomplishments:</label>
                <div class="input-group">
                    <input id="accomplishments" type="text" class="form-control" v-model="report.accomplishment" required>
                    <span class="input-group-btn">
                        <button class="btn btn-primary btn-sm" v-on:click="addItem('accomplishment')">+</button>
                    </span>
                </div>
            </div>
            <div class="form-group">
                <label for="risks">Risks:</label>
                <div class="input-group">
                    <input id="risks" type="text" class="form-control" v-model="report.risk" required>
                    <span class="input-group-btn">
                        <button class="btn btn-primary btn-sm" v-on:click="addItem('risk')">+</button>
                    </span>
                </div>
            </div>
            <div class="form-group">
                <label for="issues">Issues:</label>
                <div class="input-group">
                    <input id="issues" type="text" class="form-control" v-model="report.issue" required>
                    <span class="input-group-btn">
                        <button class="btn btn-primary btn-sm" v-on:click="addItem('issue')">+</button>
                    </span>
                </div>

            </div>
        </form>
        <div id="preview">
            <h3 class="text-muted">Preview Report</h3>
            <p class="h6">Title:
                <span class="text-muted">{{report.title}}</span>
            </p>
            <p class="h6">Accomplishments</p>
            <ul>
                <li v-for="(item, index) in report.accomplishments" class="text-muted">
                    <div v-show="!item.edit">
                        {{item.item}}
                        <button class="btn btn-danger btn-sm" v-on:click="removeItem(index, 'accomplishment')">X</button>
                        <button class="btn btn-primary btn-sm" v-on:click="editItem(index, 'accomplishment')">Edit</button>
                    </div>
                    <div v-show="item.edit">                        
                            <input type="text"  v-model="item.item">
                            <button class="btn btn-primary btn-sm" v-on:click="saveItem(index, item.item)">Save</button>
                            <button class="fa fa-camera-retro" v-on:click="item.edit = false">Cancel</button>     
                            <i class="fa fa-camera-retro fa-lg">s</i>                   
                    </div>
                </li>
            </ul>
            <p class="h6">Risks</p>
            <ul>
                <li v-for="(item, index) in report.risks" class="text-muted">{{item.item}}
                    <button class="btn btn-danger btn-sm" v-on:click="removeItem(index, 'risk')">X</button>
                </li>
            </ul>
            <p class="h6">Issues</p>
            <ul>
                <li v-for="(item, index) in report.issues" class="text-muted">{{item.item}}
                    <button class="btn btn-danger btn-sm" v-on:click="removeItem(index, 'issue')">X</button>
                </li>
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
                    { item: "Lorem ninja ipsum dolor sit amet", edit: false },
                    { item: "consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt", edit: false },
                    { item: "Ut ninja wisi enim ad minim veniam, quis nostrud", edit: false },
                    { item: "Duis ninja autem vel eum iriure dolor in hendrerit", edit: false }
                ],
                accomplishment: "",
                risks: [
                    { item: "risk one" },
                    { item: "risk two" },
                    { item: "risk threee" },
                    { item: "risk four" }

                ],
                risk: "",
                issues: [
                    { item: "issue one" },
                    { item: "issue two" },
                    { item: "issue threee" },
                    { item: "issue four" }
                ],
                issue: "",
                edit: false
            }
        }
    },
    methods: {
        removeItem: function(index, type) {
            if (type === 'accomplishment') {
                this.report.accomplishments.splice(index, 1);
            } else if (type === 'risk') {
                this.report.risks.splice(index, 1);
            } else if (type === 'issue') {
                this.report.issues.splice(index, 1);
            }
        },
        addItem: function(type) {
            if (type === 'accomplishment') {
                this.report.accomplishments.push({ item: this.report.accomplishment, edit: false });
            } else if (type === 'risk') {
                this.report.risks.push({ item: this.report.risk });
            } else if (type === 'issue') {
                this.report.issues.push({ item: this.report.issue });
            }
        },
        editItem: function(index) {
            this.report.accomplishments[index].edit = true;
        },
        saveItem: function(index, value) {
            console.log(value);
            this.report.accomplishments[index].item = value
            this.report.accomplishments[index].edit = false;
        }
    }
}
</script>

<style scoped>

</style>


