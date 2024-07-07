<script>
    let numPokemon=Math.random()*1008 + 1;
    let pokemon="https://pokeapi.co/api/v2/pokemon/"+numPokemon;
    fetch(pokemon)
    .then(res=>res.json());
    let pokname=res.name();
    let image=res.sprite;
    
    document.getElementById("button").onclick= function (){
        numPokemon=Math.random()*1008 + 1;
    }

    let h1=document.createElement("h1");
    h1.innerHTML=pokname;
    document.appendChild(h1);

    let pokimg=document.createElement("img");
    
</script>

<button id="button">Boton</button>