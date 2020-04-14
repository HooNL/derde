<template>
  <article class="container">
    <p></p>
    <section class="row">
      <!-- Stuk van linker kant met 8 cols -->
      <section class="col-md-8">
        <table class="table table-bordered table-striped">
          <thead>
            <tr>
              <th>ID</th>
              <th>Name</th>
              <th>Email</th>
              <th>Tel</th>
              <th>Adres</th>
              <th width="140">Actie</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="na in post" :key="na.id">
              <td> {{ na.id }} </td>
              <td> {{ na.naam }} </td>
              <td> {{ na.email }} </td>
              <td> {{ na.tel }} </td>
              <td> {{ na.adres }} </td>
              <td>
                <button class="btn btn-success btn-sm" @click="edit(na)">Bewerk</button>
                <button class="btn btn-danger btn-sm" @click="destroy(post.id)">Wis</button>
              </td>
            </tr>
          </tbody>
        </table>
      </section>

      <!-- Stuk van rechter kant met 4 cols -->
      <section class="col-md-4">
        <form>
          <section class="form-group">
            <label for="id">ID</label>
            <input type="text" class="form-control" v-model="input.id">
          </section>
          <section class="form-group">
            <label for="id">Naam</label>
            <input type="text" class="form-control" v-model="input.naam">
          </section>
          <section class="form-group">
            <label for="id">Email</label>
            <input type="text" class="form-control" v-model="input.email">
          </section>
          <section class="form-group">
            <label for="id">Tel</label>
            <input type="text" class="form-control" v-model="input.tel">
          </section>
          <section class="form-group">
            <label for="id">Adres</label>
            <textarea class="form-control" v-model="input.adres"></textarea>
          </section>
          <button class="btn btn-primary" v-if="savebtn" @click.prevent="save()">Opslaan</button>
          <button class="btn btn-info" v-if="updatebtn" @click.prevent="update(input.id)">Update</button>
          <button class="btn btn-danger" @click.prevent="clear()">Wissen</button>
        </form>
      </section>



    </section>
  </article>
</template>

<script>
export default {
  name: "Meld",

  data() {
    return {
      post: [],
      input: {
        id: '',
        naam: '',
        email: '',
        tel: '',
        adres: ''
      },
      savebtn: true,
      updatebtn: false
    }
  },



  created() {
    this.viuw()
    // Voor neshan dadan dar web 
    this.localData()
    this.post = JSON.parse(localStorage.getItem('aghlam'))
  },



  methods: {

    // Local data variable
    localData(){
     localStorage.setItem('aghlam', JSON.stringify(this.post))
    },


    // FN baraye kole data
    viuw(){
      this.post =  [
        { 
          id:"1",
          naam: "Hani Kamali",
          email: "hani1234@gmail.com",
          tel: "0077856231",
          adres: "Amsterdam - Netherland"
        },
        { 
          id:"2",
          naam: "Kolan  Samadi",
          email: "kolan487756@gmail.com",
          tel: "0099775431",
          adres: "New York - USA"
        },
        { 
          id:"3",
          naam: "Soghra Komando",
          email: "soghra688@hotmail.com",
          tel: "0012664564",
          adres: "Barcelona - Spanje"
        },
        { 
          id:"4",
          naam: "Fati Kostala",
          email: "hfatitafi@yahoo.com",
          tel: "0044689821",
          adres: "Kos - Yonan"
        },
      ]
    },



    // FN varaye opslaan data
    // Sakhte yek FN baraye save data
    save() {
      const id = this.input.id
      const nm = this.input.naam
      const em = this.input.email
      const tl = this.input.tel
      const ad = this.input.adres

      // Ezafeh kardane data be list
      this.post.push({
        id: id, 
        naam: nm,
        email: em,
        tel: tl,
        adres: ad
      })

      // Khali kardane veld ha bade click
      this.clear()


      // Save data ezafeh shode
      this.localData()

      // Add kardane yek alert baraye payame OK
      alert('Toegevoegd,' + " Nieuw data" + " Gelukt!")
    },


    // FN baraye verwijderen
    clear(){
        this.savebtn = true,
        this.updatebtn = false,
        this.input.id = ''
        this.input.naam = ''
        this.input.email = ''
        this.input.tel = ''
        this.input.adres = ''
    },


    // FN baraye bewerken
    edit(na){
        this.savebtn = false,
        this.updatebtn = true,
        this.input.id = na.id, 
        this.input.naam = na.naam,
        this.input.email = na.email,
        this.input.tel = na.tel,
        this.input.adres = na.adres
    },


    // FN baraye update
    update(na) {
      let mijId = na - 1
      Object.assign(this.post[mijId], this.input)
      this.clear()

      // LocalData brengen in
      this.localData()
    },


    // FN baraye delete
    destroy(na) {
      let del = this.post.indexOf(na)
      let de = this.post.splice(del, 1)
      
      console.log("Is verwijderd." + de.id);
      

      // LocalData brengen in
      this.localData()
    },


    /* 
      localStorage.setItem('aghlam', this.naam.value)
      localStorage.setItem('aghlam', this.lnaam.value)
    } */
  },
}
</script>

<style>
  @import '../bootstrap.min.css';
</style>