<template>
  <div class="row">
    <div class="col-md-6 col-md-offset-3">
      <div class="panel panel-default">
        <div class="panel-heading">
          <h3 class="panel-title">Formulaire d'inscription</h3>
        </div>
        <div class="panel-body">
          <form @submit.prevent="submit()" novalidate>
         
          <div class="columns is-multiline">
    <div class="column is-12">
        <label class="label">Email</label>
        <p class="control has-icon has-icon-right">
            <input name="email" v-model="email" v-validate.initial="'email'" class="form-control" :class="{'input': true, 'is-danger': errors.has('email') }" type="text" placeholder="Email">
            <i v-show="errors.has('email')" class="fa fa-warning"></i>
            <span v-show="errors.has('email')" class="help is-danger">{{ errors.first('email') }}</span>
        </p>
    </div>
    <div class="column is-12">
        <label class="label">Nom</label>
        <p class="control has-icon has-icon-right">
            <input name="nom" v-model="nom" v-validate.initial="'required|alpha'" class="form-control" :class="{'input': true, 'is-danger': errors.has('nom') }" type="text" placeholder="Nom">
            <i v-show="errors.has('nom')" class="fa fa-warning"></i>
            <span v-show="errors.has('nom')" class="help is-danger">{{ errors.first('nom') }}</span>
        </p>
    </div>
    <div class="column is-12">
        <label class="label">Prénom</label>
      
            <input name="prénom" v-model="prénom" v-validate.initial="'required|alpha'" class="form-control" :class="{'input': true, 'is-danger': errors.has('prénom') }" type="text" placeholder="prénom">
            <i v-show="errors.has('prénom')" class="fa fa-warning"></i>
            <span v-show="errors.has('prénom')" class="help is-danger">{{ errors.first('prénom') }}</span>
       
    </div>
    <div class="column is-12">
        <label class="label">Nom complet</label>
     
            <input :value="name" name="name" v-validate:name.initial="'required|alpha_spaces'" class="form-control" :class="{'input': true, 'is-danger': errors.has('name') }" type="text" placeholder="Nom complet">
            <i v-show="errors.has('name')" class="fa fa-warning"></i>
            <span v-show="errors.has('name')" class="help is-danger">{{ errors.first('name') }}</span>
      
    </div>
</div>
        <div class="form-group">
        <label class="control-label">Phone</label>
        
            <input name="phone" v-model="phone" v-validate="'required|numeric'"  class="form-control":class="{'input': true, 'is-danger': errors.has('phone') }" type="text" placeholder="Phone">
            <i v-show="errors.has('phone')" class="fa fa-warning"></i>
            <span v-show="errors.has('phone')" class="help is-danger">{{ errors.first('phone') }}</span>
      
    </div>

           

            <div class="form-group" :class="{ 'has-error': errors.has('age') }">
              <label class="control-label" for="age">Age</label>
              <input name="age" type="number" class="form-control" id="age" placeholder="Age" v-validate data-rules="required|age:10">
              <span v-show="errors.has('age')" class="help-block">
                {{ errors.first('age') }}
              </span>
            </div>
         
            <div class="form-group" >
              <label class="control-label" >Adresse</label>
               <input type="text" class="form-control" placeholder="Adresse" aria-label="Adresse" aria-describedby="basic-addon1">
            </div>
            <div class="form-group" >
              <label class="control-label" >Type de visite</label>
               <input type="text" class="form-control" placeholder="Type de visite" aria-label="Typevisite" aria-describedby="basic-addon1">
            </div>
             <div class="form-group" >
              <label class="control-label" >Médecin</label>
               <input type="text" class="form-control" placeholder="Médecin" aria-label="Médecin" aria-describedby="basic-addon1">
            </div>
             <div class="form-group" >
              <label class="control-label" >Date de visite</label>
               <input type="date" class="form-control" placeholder="Date de visite" aria-label="Datevisite" aria-describedby="basic-addon1">
            </div>
            <div class="form-check">
              <label class="form-check-label">
                <input class="form-check-input" type="radio" name="Célébataire" id="Célébataire" value="option1" >
                Célébataire
              </label>
              <label class="form-check-label">
                <input class="form-check-input" type="radio" name="Marié" id="Marié" value="option1" >
                Marié(e)
              </label>
              <label class="form-check-label">
                <input class="form-check-input" type="radio" name="Veuf" id="Veuf" value="option1" >
                Veuf(ve)
              </label>
              <label class="form-check-label">
                <input class="form-check-input" type="radio" name="Séparé" id="Séparé" value="option1" >
                Séparé(e)
              </label>
              <label class="form-check-label">
                <input class="form-check-input" type="radio" name="Divorcé" id="Divorcé" value="option1" >
                Divorcé(e)
              </label>
            </div>
           

       

            <button type="submit" class="btn btn-default">Submit</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
 
  data: () => ({
    email: '',
    first_name: '',
    last_name: ''
  }),
  computed: {
    name() {
      return `${this.first_name} ${this.last_name}`;
    }
  },
  methods: {
    submit() {
      if(!this.validate()) {
        alert('Submitted')
      } else {
        alert('Not Submitted')
      }
    },
    validate() {
      this.$validator.validateAll();

      return this.errors.any();
    }
  }
}
</script>

<style>
.panel {
  margin-top: 2em;
}
label{color:  #191970}
background{color:#FFE4E1;}
button{
color:white;
background: #191970;}
</style>
