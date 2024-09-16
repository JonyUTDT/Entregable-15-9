<!-- Codigo JS -->

<script>
  import * as d3 from "d3"
  import Waffles from "./lib/Waffles.svelte"
  import IrregularPath from "./lib/IrregularPath.svelte"
  import CoffeColumns from "./lib/CoffeColumns.svelte"
  import Donas from "./lib/Donas.svelte"
  import IsotypeBars from "./lib/IsotypeBars.svelte"

  let numbers = [21, 33, 42, 54, 63, 71, 77, 84, 92, 98]
  let numeros = [23, 35, 45, 56, 50, 43, 38, 32, 28, 25]
  let anos = [2014, 2015, 2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023]
  let movrojo = [90, 88, 97, 85, 85, 86, 86, 86, 86, 86] 
  let movazul = [90, 88, 97, 85, 85, 86, 91, 89, 91, 91]
  let izquierda = [95, 93, 95, 93, 93, 94, 94, 93, 93, 95]

  /* Escala lineal para las alturas de los isotipos */
  function altura(n) {
    let scale = d3
      .scaleLinear()
      .domain([5, 100]) // [mínimo, máximo]
      .range([15, 225]) // [altura_minima, altura_máxima]
    return scale(n)
  }

  /* Escala lineal para los angulos de los medidiores*/
  function angulo(i) {
    let scale = d3
      .scaleLinear()
      .domain([5, 100]) // [Minimo(De la lista), Maximo(De la lista)]
      .range([-70, 70]) // [Angulo Maximo, Angulo Minimo]. Pongo estos valores ya que la flecha esta centrada en el 50% del tablero
    return scale(i)
  }

  function angulo1(j) {
    let scale = d3
      .scaleLinear()
      .domain([5, 100]) // [Minimo(De la lista), Maximo(De la lista)]
      .range([-70, 70]) // [Angulo Maximo, Angulo Minimo]. Pongo estos valores ya que la flecha esta centrada en el 50% del tablero
    return scale(j)
  }
</script>

<svelte:head>
  <iframe src='https://flo.uri.sh/story/2592577/embed' title='Interactive or visual content' class='flourish-embed-iframe' frameborder='0' scrolling='no' style='width:100%;height:600px;' sandbox='allow-same-origin allow-forms allow-scripts allow-downloads allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation'></iframe><div style='width:100%!;margin-top:4px!important;text-align:right!important;'><a class='flourish-credit' href='https://public.flourish.studio/story/2592577/?utm_source=embed&utm_campaign=story/2592577' target='_top' style='text-decoration:none!important'><img alt='Made with Flourish' src='https://public.flourish.studio/resources/made_with_flourish.svg' style='width:105px!important;height:16px!important;border:none!important;margin:0!important;'> </a></div>
  <iframe src='https://flo.uri.sh/story/2592457/embed' title='Interactive or visual content' class='flourish-embed-iframe' frameborder='0' scrolling='no' style='width:100%;height:600px;' sandbox='allow-same-origin allow-forms allow-scripts allow-downloads allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation'></iframe><div style='width:100%!;margin-top:4px!important;text-align:right!important;'><a class='flourish-credit' href='https://public.flourish.studio/story/2592457/?utm_source=embed&utm_campaign=story/2592457' target='_top' style='text-decoration:none!important'><img alt='Made with Flourish' src='https://public.flourish.studio/resources/made_with_flourish.svg' style='width:105px!important;height:16px!important;border:none!important;margin:0!important;'> </a></div>
</svelte:head>

<!-- HTML -->
<main>
  <br class="container">
    <h1 style="text-align: center;">¡Shell Arrasa!</h1>
    <p style="text-align: center; font-size: 16px;">Cómo conquistó el mercado petrolero y dejó a YPF en el polvo</p>
    <br>
    <br>
    <div class="TextosContenedor">
    <h3 style="text-align: left;">Ventas de tanques de nafta de las empresas <span class="YPF">YPF</span> y <span class="Shell">Shell</span> en los ultimos 10 años.</h3>
    <p style="text-align: left; font-size: 16px;"> Medidas en millones</p>
    </div>

    <p style="text-align: center; font-size: 22px; font-weight: bold;">Referencia</p>
    <img
      class="Referencia"
      src="./images/Referencia.svg"
      alt=""
      style="display: block; margin: 0 auto; width: 17%; height: 17%"
    />
    <br>
    <br>
    <br>
    <br>
    <!-- Medidior de Nafta -->
    <div>
      <div class = "Ilustracion">
        <!-- El #each va agarrando cada numero de numbers de a uno y se lo pasa al resto del codigo como i. Es como un if de TD, que agarra al i empezando de la posicion 0 de la lista y frena cuando supera al valor del utimo elemento de la lista -->
        {#each numbers as i, index}
        <div class = "MedidoresconTexto">  
          <!-- Div que contiene a las imagenes, Medidiores y Agujas -->
          <div class="MedidoresCompletos">             
            <!-- Imagen del Medidior -->  
            <img 
                class = "Medidores" 
                src = "./images/Component 10.svg" 
                alt =""
              />
              <!-- Imagen de la Aguja -->
              <img 
                class = "Agujas"
                style="transform: rotate({angulo(i)}deg); transform-origin: center {movrojo[index]}%; left: {izquierda[index]}px;" 
                src="./images/Vector Rojo.svg" 
                alt=""
              />
              <img 
                class = "Agujas"
                style="transform: rotate({angulo1(numeros[index])}deg); transform-origin: center {movazul[index]}%; left: {izquierda[index]}px;" 
                src="./images/Vector Azul.svg" 
                alt=""
              />
          </div>
        <!-- Texto de cada numbers[i] -->
          <p><strong>{anos[index]}</strong></p>
        </div>
        {/each}
      </div>
    </div>
    
    <br>
    <div class = "TextosContenedor">
    <p style = "text-align: left; font-size: 20px;"> A diferencia de YPF, que sufrió una baja del 10,7% en sus ventas en 2018, Shell aumentó sus ventas gracias a precios más competitivos. Esto provocó que, a partir de ese año, YPF se viera obligado a cerrar más sucursales que Shell. YPF (hasta la fecha) no ha podido recuperarse de esa caída.</p>
    </div>
    <br>
    <br>
    <br>
    <div class = "GraficosComplementarios">
      <iframe src='https://flo.uri.sh/story/2592457/embed' title='Interactive or visual content' class='flourish-embed-iframe' frameborder='0' scrolling='no' style='width:100%;height:600px;' sandbox='allow-same-origin allow-forms allow-scripts allow-downloads allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation'></iframe><div style='width:100%!;margin-top:4px!important;text-align:right!important;'><a class='flourish-credit' href='https://public.flourish.studio/story/2592457/?utm_source=embed&utm_campaign=story/2592457' target='_top' style='text-decoration:none!important'><img alt='Made with Flourish' src='https://public.flourish.studio/resources/made_with_flourish.svg' style='width:105px!important;height:16px!important;border:none!important;margin:0!important;'> </a></div>
      <iframe src='https://flo.uri.sh/story/2592577/embed' title='Interactive or visual content' class='flourish-embed-iframe' frameborder='0' scrolling='no' style='width:100%;height:600px;' sandbox='allow-same-origin allow-forms allow-scripts allow-downloads allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation'></iframe><div style='width:100%!;margin-top:4px!important;text-align:right!important;'><a class='flourish-credit' href='https://public.flourish.studio/story/2592577/?utm_source=embed&utm_campaign=story/2592577' target='_top' style='text-decoration:none!important'><img alt='Made with Flourish' src='https://public.flourish.studio/resources/made_with_flourish.svg' style='width:105px!important;height:16px!important;border:none!important;margin:0!important;'> </a></div>
    </div>
    <br>
    <br>
    <br>
    <div class="Footer">
    <img style ="width: 10%; height: 10%" src="./images/LogoDiTella.png" alt=""/>
    <p>Proyecto 1 VD</p>
    <p>Alumno: Jonathan Jeifetz</p>
    <p>Universidad: Torcuato Di Tella</p>
    <p>Mail: <u>jjeifetz@mail.utdt.edu</u></p>
    </div>
</main>

<!-- Codigo CSS -->

<style>
  .container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 2rem;
  }

  .flourish-embed{
    flex-basis: 50%;
  }

  
  .Ilustracion{
    /*position: relative;
    display: flex;
    flex-direction: row;*/
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: space-between;
    width: 100%;
    margin: auto;
  }
  .MedidoresCompletos {
    position: relative;
    width: 200px;
    height: 115px;
    text-align: center;
  }
  .Medidores {
    /*position: relative;
    display: flex;
    flex-direction: row;*/
    /*position: absolute;*/
    width: 100%;
    height: 100px;
  }
  .Agujas {
    /*position: relative;
    transform-origin: left bottom;
    display: flex;
    flex-direction: row;*/
    position: absolute;
    /*left: 47.5%;*/
    bottom: 25px;
    height: 65px;
    
    
    transform-origin: center 93%;
    /*transform: translateX(-50%) rotate(0deg);
    height: auto;*/
  }

  .MedidoresconTexto p {
    text-align: center  ;
    /*left: 30%;
    right: 90%;*/
    height: 5px;
    margin: -5px;
  }

  .MedidoresconTexto {
    margin-bottom: 50px;
  }

  .YPF {
    color: #0B5CBC;
  }

  .Shell {
    color: #E21515;
  }

  .GraficosComplementarios {
    display: flex;
  }

  .TextosContenedor {
    width: 50%;
    margin: 0 auto;
  }
  /*.flourish-embed2 {
    width: 50%;
  }*/

  .Footer{
    text-align: center;
    font-size: 10px;
    line-height: 0;
    width: 35%;
    margin: 0 auto;
  }
</style>






<!-- Rotacion de la aguja -->
 <!-- .person {
  trensform: rotate({number});
  transform-origin: bottom;
} -->


<!-- 
 <div class = "Agujas">  
    {#each numbers as i}
      <img 
        style="transform: rotate({angulo(i)}deg);" 
        src="./images/Vector.svg" 
        alt=""
      />
    {/each}
    -->


    <!--
      <div>
    <div class = "Ilustracion">
      {#each numbers as i}
        <img class = "Medidores" src = "./images/Component 10.svg" alt =""/>
        <img 
          class = "Agujas"
          style="transform: rotate({angulo(i)}deg);"
          src="./images/Vector.svg" 
          alt=""
        />
        <p>{i}</p>
      {/each}
    </div>
  </div>
  -->