<template>
        <form @submit.prevent="sendData()">
            <div class="form-control">
                <label for="name">Name</label>
                <input v-model.trim="this.student.name" type="text" placeholder="ณัฐวุฒิ สอนเขียว" />
                <!-- <input @keyup.enter="ฟังก์ชั่นต่างๆ" type="text" placeholder="ณัฐวุฒิ สอนเขียว" /> -->
                <!-- กด enter ก็ทำฟังก์ชั่นได้  -->
            </div>

            <div class="form-control">
                <label for="id">Student ID</label>
                <input v-model.trim="this.student.id" type="text" placeholder="64070148" />
            </div>

            <div class="form-control">
                <h2>Gender</h2>
                <div>
                    <input type="radio" value="ชาย" v-model="student.gender" checked>
                    <label for="male">Male</label>
                </div>
                
                <div>
                    <input type="radio" value="หญิง" v-model="student.gender">
                    <label for="male">Female</label>
                </div>

            </div>

            <div class="form-control">
                <label for="kana">faculty</label>
                <select v-model="student.branch">
                    <option value="เทคโนโลยีสารสนเทศ">Infomation Technology</option>
                    <option value="วิศวะ">Engineer</option>
                </select>

            </div>

            <div v-if="this.student.branch === 'เทคโนโลยีสารสนเทศ'" class="form-control">
                <label for="saka">Branch</label>
                <select v-model="this.student.saka">
                    {{ setSaka }}
                    <option value="เทคโนโลยีสารสนเทศ">Infomation Technology</option>
                    <option value="DSBA">DSBA</option>
                    <option value="BIT">BIT</option>
                </select>
            </div>

            <div v-else class="form-control">
                <label for="saka">Branch</label>
                <select v-model="this.student.saka">
                    {{ setSaka }}
                    <option value="วิศวะคอม">Computer Engineer</option>
                    <option value="วิศวะแมคคา">Mechatronics Engineer</option>
                    <option value="วิศวะเคมี">Chemical Engineer</option>
                </select>
            </div>

            <div class="control-button" >
                <button>ลงทะเบียน</button>
                <!-- <button :disabled="student.name.length < 1">ลงทะเบียน</button> -->
                <!-- จะ disable button ถ้าตรงเงื่อนไขด้านใน -->
            </div>
            
        </form>

       <!-- {{ JSON.stringify(student) }} -->
</template>

<script>
export default {
    name: "FromComponent",
    data() {
        return {
            student: {
                name: "",
                id: "",
                branch: "เทคโนโลยีสารสนเทศ",
                saka: "เทคโนโลยีสารสนเทศ",
                gender: "ชาย",
                isVisible: false
            }
        }
    },
    methods: {
        sendData(){
            if(this.student.name === "" || this.student.id === "" || isNaN(parseInt(this.student.id))){
                alert("fill the form correctly")
            }
            else{
                const newStudent = {
                    name : this.student.name,
                    id: this.student.id,
                    branch: this.student.branch,
                    saka: this.student.saka,
                    gender: this.student.gender,
                    isVisible: false
                }
                this.$emit("save", newStudent)
                this.resetForm()
            }
            

        },
        resetForm(){
            this.student.name = "",
            this.student.id = "",
            this.student.branch = "เทคโนโลยีสารสนเทศ",
            this.student.saka = "เทคโนโลยีสารสนเทศ",
            this.student.gender = "ชาย"
            
        }

    },
    computed: {
        setSaka() {
            // eslint-disable-next-line vue/no-side-effects-in-computed-properties
            return this.student.branch === "เทคโนโลยีสารสนเทศ" ? this.student.saka = "เทคโนโลยีสารสนเทศ" : this.student.saka = "วิศวะคอม"
        }
    }
}
</script>

<style scoped>
    form{
    margin:2rem auto;
    max-width: 40rem;
    border-radius: 12px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.25);
    padding: 2rem;
    background: #fff;
}
.form-control{
    margin: 0.5rem 0;
}
label{
    font-weight: bold;
}
input,select{
    display: block;
    width: 100%;
    font:inherit;
    margin-top: 0.5rem;
}
button{
    font:inherit;
    background: orangered;
    color:white;
    cursor: pointer;
    margin-top: 1rem ;
    padding: 0.5rem 1rem;
    border-radius: 15px;
    
}
.control-button{
    display: flex;
    align-items: center;
    justify-content: center;
}
input[type="radio"]{
    width: auto;
    display: inline-block;
    margin-right: 0.6rem;
}
input[type="radio"]+label{
    font-weight: normal;
}
h2{
    font-size: 1rem;
    margin: 0.5rem 0;

}

</style>
