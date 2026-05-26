# 🚀 Perfil Profesional - Izan Martínez Hurtado

## 👤 Sobre Mí
¡Hola! Mi nombre es **Izan Martínez Hurtado** y soy estudiante de **2º de Ciclo Formativo de Grado Superior en Desarrollo de Aplicaciones Web (DAW)** en el *Institut Les Salines*. 

Me considero un apasionado del desarrollo de software, la optimización de código y el diseño de arquitecturas Web modernas, adaptables y eficientes. Mi enfoque principal está en comprender a fondo la lógica del cliente y asegurar que las interfaces interactúen de manera nativa y fluida con el usuario.

---

## 🛠️ Habilidades Técnicas (Stack Tecnológico)

A lo largo de mi trayectoria académica y proyectos personales, he consolidado habilidades en las siguientes tecnologías:

| Área | Tecnologías |
| :--- | :--- |
| **Desarrollo Front-End** | HTML5, CSS3, JavaScript (ES6+), Maquetación Responsive |
| **Lógica y Arquitectura** | Programación Orientada a Objetos (POO) en JavaScript |
| **Entornos y Herramientas**| Git, GitHub, Visual Studio Code |
| **Documentación y Calidad**| JSDoc, Pruebas Unitarias, Clean Code |

---

## 💻 Proyecto Destacado: RayaManía (Juego del 3 en Raya)

**RayaManía** es una aplicación interactiva desarrollada completamente en JavaScript nativo utilizando el paradigma de la **Programación Orientada a Objetos (POO)**. Separa de forma estricta la interfaz gráfica de usuario (DOM) de la lógica interna del motor del juego.

### 📐 Arquitectura del Sistema
El proyecto se compone de los siguientes módulos estructurados en clases:
* **`clsTableroApp`**: Controlador de interfaz que gestiona las vistas de inicio, pantallas de juego, turnos y el botón de reinicio.
* **`clsEngine`**: El núcleo lógico del juego que procesa las reglas, analiza combinaciones de victoria y coordina las acciones de la Inteligencia Artificial.
* **`clsTablero`**: Clase encargada de agrupar y orquestar las casillas de juego.
* **`clsCelda`**: Abstracción individual de cada casilla del tablero para detectar interacciones.
* **`clsJugadores` & `clsJugador`**: Gestores de identidades para diferenciar las partidas locales de 2 jugadores o partidas contra la IA (*Maestro IA*).

---

## 📝 Muestra de Código Auto-Descriptivo

A continuación, se adjunta un fragmento del núcleo del juego donde se implementa la máquina que analiza el estado de las celdas en tiempo real:

```javascript
/**
 * Ejecuta el movimiento automatizado de la Inteligencia Artificial (Máquina), 
 * buscando la primera celda libre dentro del tablero actual.
 * * @author Izan Martinez Hurtado
 * @version 1.0.0
 */
jugadaMaquina() {
    // Recorrer la lista de celdas y evaluar su estado de bloqueo
    for (let i = 0; i < this.tablero.celdas.length; i++) {
        let celda = this.tablero.celdas[i];
        
        // Si encontramos una celda libre (false), la IA realiza su jugada y la bloquea
        if (this.tablero.celdas[i].bloqueada == false) {
            celda._html_cell.className = "celda_click_O";
            celda.bloqueada = "Maestro IA";
            break; // Interrumpe el ciclo una vez colocada su ficha
        }
    }
    this.comprobarWin("Maestro IA"); // Evalúa si esta acción desencadena una victoria
    this.cambiarTurno();            // Devuelve el control del turno al jugador humano
}
