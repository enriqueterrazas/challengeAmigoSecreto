# challengeAmigoSecreto
codigo para sortear nombres de amigos al azar

//Array para almacenar nombres de amigos.
let amigos=[];

//Funcion agregar amigos
function agregarAmigo(){
    const inputAmigo = document.getElementById('amigo');
    const nombreAmigo = inputAmigo.value.trim();


    //validar que el campo no  vacio
    if(nombreAmigo === ""){
        alert("Favor de escribir un nombre.");
        return;
    }

    //nombre no duplicado
    if(amigos.includes(nombreAmigo)){
        alert(`El nombre ${nombreAmigo}ya esta en la lista`);
        return;
    }        

    //agregar nombre array amigos
    amigos.push(nombreAmigo);

    //limpiar campo de entrada
    inputAmigo.value = "";  

    //actualizar lista HTML
    actualizarLista();

}

//funcion actualizar lista de amigos interfaz
function actualizarLista(){
    const listaAmigos = document.getElementById('listaAmigos');

    //limpiar contenido actual lista
    listaAmigos.innerHTML = "";

    //recorrer array for
    for(let i = 0; i <amigos.length; i++){
        const li = document.createElement('li');
        li.textContent = amigos[i];
        listaAmigos.appendChild(li);

    }
}

//funcion para seleccionar amigo aleatorio
function sortearAmigo(){
    if(amigos.length === 0){
        alert("No hay amigos para sortear, agrega un nombre.");
        return;
    }

    //generar indice aleatorio
    const indiceAleatorio = Math.floor(Math.random() * amigos.length);
    const amigoSorteado = amigos[indiceAleatorio];

    //mostrar resultado HTML
    const resultado = document.getElementById('resultado');
    resultado.innerHTML = `Amigo sorteado: <strong>${amigoSorteado}</strong>`;

}
