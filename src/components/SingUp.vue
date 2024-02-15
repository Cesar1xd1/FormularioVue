<script>


    export default{


    
        data(){
            return{
                nControl:'',
                nombre: '',
                edad: '',
                semestre: '',
                carrera: '',
                alumnos: [],
                checkedE: [],
                checkedA: [],
            }
        },
        methods:{
            aceptar(){
                var datos = {
                    nControl: this.nControl,
                    nombre: this.nombre,
                    edad: this.edad,
                    semestre: this.semestre,
                    carrera: this.carrera,
                    checkedE: this.checkedE,
                    checkedA: this.checkedA
                };
                this.alumnos.push(datos);
                this.nControl = '';
                this.nombre = '';
                this.edad = '';
                this.semestre ='';
                this.carrera = '';
                this.checkedE = [];
                this.checkedA = [];
            }
        }
    }
    
</script>

<template>
    <h3>Formulario de Alumnos</h3>
    <form @submit.prevent="aceptar">
        <label class="lab">Numero de Control</label>
        <input class="inp" type="number" required v-model="nControl">

        <label class="lab">Nombre Completo</label>
        <input class="inp" type="text" required v-model="nombre">

        <label class="lab">edad</label>
        <input class="inp" type="number" required v-model="edad">

        <label class="lab">Semestre</label>
        <input class="inp" type="number" required v-model="semestre">

        <label class="lab">Carrera</label>
        <select class="inp"  v-model="carrera" required>
            <option>ISC</option>
            <option>IM</option>
            <option>IIA</option>
            <option>CP</option>
            <option>LA</option>
        </select>
        
        

        <label class="lab">Especialidades</label>
        <div class="especialidades">
            <input type="checkbox" id="ingdatos" value="Ingenieria de Datos" v-model="checkedE">
            <label for="ingdatos">Ingenieria de Datos</label>
            <br>
            <input type="checkbox" id="devops" value="Devops" v-model="checkedE">
            <label for="devops">Devops</label>
            <br>
            <input type="checkbox" id="redes" value="Redes" v-model="checkedE">
            <label for="redes">Redes</label>
            <br>
        </div>
        <label class="lab">Actividades Extraescolares</label>
        <div class="actividadesE">
            <input type="checkbox" id="deportes" value="Deportes" v-model="checkedA">
            <label for="deportes">Deportes</label>
            <br>
            <input type="checkbox" id="danza" value="Danza" v-model="checkedA">
            <label for="danza">Danza</label>
            <br>
            <input type="checkbox" id="desfile" value="Desfile" v-model="checkedA">
            <label for="desfile">Desfiles</label>
            <br>
        </div>
        



        <div class="submit">
            <button class="btn btn-success">Aceptar</button>
        </div>
    </form>    
    
    <div class="container">
        <table class="table" id="t" >
        <thead>
            <tr>
                <th>Num. Control</th>
                <th>Nombre</th>
                <th>Edad</th>
                <th>Semestre</th>
                <th>Carrera</th>
                <th>Materias de Espcialidad</th>
                <th>Actividades Extraescolares</th>
            </tr>
        </thead>
                <tr v-for="a in alumnos" v-bind:key="a">
                    <td>{{ a.nControl }}</td>
                    <td>{{ a.nombre }}</td>
                    <td>{{ a.edad }}</td>
                    <td>{{ a.semestre }}</td>
                    <td>{{ a.carrera }}</td>
                    <td><p v-for="e in a.checkedE">{{ e }}</p></td>
                    <td><p v-for="ae in a.checkedA">{{ ae }}</p></td>
                </tr>
    </table>
    </div>
    
</template>

<style>
    form{
        max-width: 420px;
        margin: 30px auto;
        background: white;
        text-align: left;
        padding: 40px;
        border-radius: 10px;
    }
    .lab{
        color:#111195;
        display: inline-block;
        margin: 25px 0 15px;
        font-size: 1em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
        
    }
    .inp{
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
        font-size: 20px;
        background-color: bisque;
    }
    button{
        background-color: #34b34d; 
        margin-left: 50%;
        transform: translateX(-50%);
        margin-top: 20px;
        width: 100px;
        height: 40px;
    }
    #t {
        font-family: Arial, Helvetica, sans-serif;
        border-collapse: collapse;
        width: 80%;
        margin: 20px auto;
        
    }
    
    #t td, #t th {
        border: 1px solid #ddd;
        padding: 8px;
    }

    #t tr:nth-child(even){background-color: #f2f2f2;}

    #t tr:hover {background-color: #ddd;}
    
    #t th {
        padding-top: 12px;
        padding-bottom: 12px;
        text-align: left;
        background-color: #04AA6D;
        color: white;
    }
    h3{
        color: black;
        font-size: 40px;
    }
    p{
        border: 0 ;
    }
</style>