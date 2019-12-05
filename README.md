# Penguin Jumps - Proyecto de Teoría Computacional

* **José Ángel Navarro Almendárez - 160963**

* **Profesor: Juan Carlos González Ibarra**


## Lenguaje

El lenguaje de programación utilizado para este proyecto es **Rust**.

Se utiliza **Rust** para compilar a un binario `.wasm`, que finalmente es tecnología **WebAssembly**. Esto indica decir que es una aplicación Web.

Como herramientas secundarias se uso **HTML** y **Bootstrap 4** para darle diseño y **JavaScript** para agregar música y efectos de sonido, así comomostrar en pantalla los movimientos que va haciendo el personaje del juego.

## Instalación

Para poder llevar a cabo la ejecución de este proyecto se deben tener varios puntos en consideración:

#### 1. Lenguaje Rust

Se debe descargar e instalar el lenguaje [**Rust**](https://www.rust-lang.org/tools/install "Instalación"), cuya instalación dependerá del sistema operativo.
*Las pruebas se hicieron en un entorno Linux y se recomienda su uso para facilidad de pruebas*.

#### 2. Compilador WASM

Para poder compilar nuestro código Rust a código **WebAssembly** necesitamos instalar esa opción de compilación, para ello usaremos `rustup` ejecutando los siguientes comandos en la terminal:

	rustup install nightly
	rustup target add wasm32-unknown-unknown
	rustup update
	cargo +nightly install wasm-bindgen-cli
	cargo install -f cargo-web

#### 3. Comprobación

Para verificar su correcta instalación se puede correr el comando en la terminal:

	cargo web --version

#### 4. Iniciar el servicio

Para comprobar que ya no hay problemas al correr una aplicación de estas se debe ir a la carpeta del proyecto y correr el siguiente comando:

	cargo web start --target=wasm32-unknown-unknown

Se creará un servidor local en donde se podrá correr el proyecto en  `localhost:8000` o el puerto que marque en la terminal.

La primera vez que se ejecuta descargará automáticamente todos los paquetes necesarios y podría tomar un tiempo.

## Penguin Jumps

El proyecto trata de un pingüino que está en pantalla y que deberá de saltar por ellas para ir recolectando peces que aparecen en la esquina superior derecha. Para recolectarlos solo es necesario tocarlos y el puntaje se autoicrementará.

Inicialmente dispone de dos vidas, que están marcadas en la parte superior izquiera de la pantalla, pero a lo largo del juego puden ir apareciendo más, aunque para recolctarlas es necesario pararse sobre ellas y presionar el botón hacia abajo. Se pueden acumular un máximo de 4 vidas.

Tanto los peces, como las vidas y las plataformas (tanto ancho como posición) aparecerán aleatoriamente en pantalla.

Conforme se vayan recolectando peces la velocidad de las plataformas irá aumentando de la siguiente manera:

* 10 Peces la velocidad se aumenta al doble
* 50 Peces la velocidad se aumenta al doble
* 100 Peces la velocidad se aumenta al doble
* 175 Peces la velocidad se aumenta al doble

El objetivo es juntar la mayor cantidad de peces.

### Controles de movimiento

| Tecla | Función |
|-|-|
Up, W | Saltar
Down, S | Agacharse
Left, A | Moverse a la izquierda
Right, D | Moverse a la derecha
SPACE | Comenzar/Reiniciar partida
S + W, Down + Up | Bajar plataforma
