<template>
  <div>
    <v-container>
      <v-layout row wrap>
        <v-flex md3 text-xs-center class="px-1">
          <v-card dark color="primary">
            Name
          </v-card>
        </v-flex>
        <v-flex md3 text-xs-center class="px-1">
          <v-card dark color="primary">
            Email
          </v-card>
        </v-flex>
        <v-flex md1 text-xs-center class="px-1">
          <v-card dark color="primary">
            Age
          </v-card>
        </v-flex>
        <v-flex md2 text-xs-center class="px-1">
          <v-card dark color="primary">
            Roll Number
          </v-card>
        </v-flex>
        <v-flex md3 text-xs-center class="px-1">
          <v-card dark color="primary">
            Actions
          </v-card>
        </v-flex>      </v-layout>
      <v-layout row wrap v-for="(std,i) in students" :key="i">
        <v-flex md3 text-xs-center class="px-1 mt-2">
          <v-card color="green">
            {{std.name}}
          </v-card>
        </v-flex>
        <v-flex md3 text-xs-center class="px-1 mt-2">
          <v-card color="green">
            {{std.email}}
          </v-card>
        </v-flex>
        <v-flex md1 text-xs-center class="px-1 mt-2">
          <v-card color="green">
            {{std.age}}
          </v-card>
        </v-flex>
        <v-flex md2 text-xs-center class="px-1 mt-2">
          <v-card color="green">
            {{std.rollNo}}
          </v-card>
        </v-flex>
        <v-flex md3 text-xs-center>
          <v-btn small flat color="red" class="mt-1" @click="onDelete(std,i)"> Delete </v-btn>
          <v-btn small flat color="red" class="mt-1 ml-2" @click="onEdit(std,i)"> Edit </v-btn>
        </v-flex>

      </v-layout>
    </v-container>
    <v-layout row wrap>
      <v-flex offset-md4 md4>
        <v-text-field
          v-model="name"
          label="Name"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row wrap>
      <v-flex offset-md4 md4>
            <v-text-field
            v-model="email"
            label="E-mail"
          ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row wrap>
      <v-flex offset-md4 md4>
        <v-text-field
          v-model="age"
          label="Age"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row wrap>
      <v-flex offset-md4 md4>
        <v-text-field
          v-model="rollNo"
          label="Roll Number"
        ></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row wrap>
      <v-flex offset-md4 md4>
            <v-btn @click="submit">submit</v-btn>
            <v-btn @click="clear">clear</v-btn>
      </v-flex>
    </v-layout>
      <form>
  </form>
  </div>
</template>

<script>
  export default {
    data: () => ({
      name: '',
      email: '',
      age: null,
      rollNo: '',
      editClicked: false,
      indexTrack: null,
      students: [
        {name: 'ibad', email: 'ibad@gmail.com', age: 34, rollNo: 'RM3929'},
        {name: 'ali', email: 'ali@gmail.com', age: 24, rollNo: 'RM3859'},
        {name: 'asad', email: 'asad@gmail.com', age: 16, rollNo: 'RM9594'},
        {name: 'fida', email: 'fida@gmail.com', age: 18, rollNo: 'RM9594'},
        {name: 'Nida', email: 'nida@gmail.com', age: 26, rollNo: 'RM9594'},
        {name: 'John', email: 'john@gmail.com', age: 19, rollNo: 'RM9594'}
      ]
    }),

    methods: {
      onDelete (student,index) {
        console.log("student has been deleted", student)
        this.indexTrack = index
        this.students.splice(index,1)
      },
      onEdit (student,index) {
        this.indexTrack = index
        this.editClicked = true
        this.name = student.name
        this.age = student.age
        this.rollNo = student.rollNo
        this.email = student.email
        console.log("student has Edit", index)
      },
      submit () {
        console.log('form submitted')
        let obj = {
          name: this.name,
          age: this.age,
          email: this.email,
          rollNo: this.rollNo
        }
        if(this.editClicked) {
        this.students[this.indexTrack] = obj
        } else {
        this.students.push(obj)
        }
        this.editClicked = false
        this.name = ''
        this.age = null
        this.email = ''
        this.rollNo = ''
      },
      clear () {
        console.log('clear')
      }
    }
  }
</script>
