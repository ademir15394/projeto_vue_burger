<template>
  
<div>

    <Message :msg="msg" v-show="msg"/>


    <div>

        <form id="form_component" @submit="createBurguer">

            <div class="input_container">

                <label for="name"> Nomer do Cliente</label>

                <input type="text" id="nome" name="name" v-model="nome" placeholder="Digite Seu Nome">

            </div>

            <div class="input_container">

                 <label for="pao"> Tipo de pão</label>

                 <select name="pao" id="pao" v-model="pao">
                
                    <option value="">Selecione seu pao</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>

                </select>
                 
            </div>

            <div class="input_container">

                <label for="carne"> Tipo de carne</label>

                <select name="carner" id="carne" v-model="carne">

                <option value="">Selecione seu pao</option>
                <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{carne.tipo}}</option>

                </select>

            </div>

            <div class="input_container" id="opcionais-container">

                <label for="name"> Selecione os opicionais:</label>
                <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">

                    <input id="opcionais-title" type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">

                    <span>{{opcional.tipo}}</span>

                </div>

                <input type="submit" class="submit-btn" value="Criar seu Burguer">
            </div>

        </form>

    </div>

</div>

</template>

<script>
import Message from "./Message.vue"

export default {

    name: "Banner_form",

    data(){
        return{
            paes:null,
            carnes:null,
            opcionaisdata:null,
            nome:null,
            pao:null,
            carne:null,
            opcionais:[],
            msg:null
        }
    },

    methods:{
        async getIgredientes(){
            const req = await fetch("http://localhost:3000/ingredientes");
            const data = await req.json();

            this.paes = data.paes;
            this.carnes = data.carnes;
            this.opcionaisdata = data.opcionais;

        },

        async createBurguer(e){

            e.preventDefault();

            const data = {
            nome: this.nome,
            pao: this.pao,
            carne: this.carne,
            opcionais: Array.from(this.opcionais),
            status: "Solicitado",
            };

            const dataJson = JSON.stringify(data);

            const req = await fetch("http://localhost:3000/burgers", {
                method: "POST",
                headers:{"content-type": "application/json"},
                body: dataJson
            }); 

            const res = await req.json();
            console.log(res);

            this.msg = `Seu pedido esta pronto ${res.id}`

            setTimeout(() => this.msg = "", 3000)

            this.nome = "";
            this.carne = "";
            this.pao = "";
            this.opcionais = "";
        }
    },
    mounted(){
        this.getIgredientes()
    },
    components:{
        Message,
    }
}
</script>

<style acoped>

#form_component{
    max-width:400px;
    margin: 0 auto;
}

.input_container{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}

label{
    font-weight: bold;
    margin-bottom: 15px;
    color:#222;
    padding: 5px 10px;
    border-left: 4px solid #FCBA03;
}

input, select{
    padding: 5px 10px;
    width: 300px;
}

#opcionais-container{
    flex-direction:row;
    flex-wrap: wrap;
}

#opcionais-title{
    width: 14%;
}

.checkbox-container{
    display:flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 25px;
}

.checkbox-container span,
.checkbox-container input{
    width: auto;
}

.checkbox-container span{
    margin-left: 6px;
    font-weight: bold;
}

.submit-btn{
    background-color:#222;
    color:#FCBA03;
    font-weight:bold;
    border:2px solid #222;
    padding:10px;
    font-size: 16px;
    margin: 0 auto;
    cursor:pointer;
    transition: .5s;
}


.submit-btn:hover{
    background-color:transparent;
    color:#222;
}

</style>