[![Build and Deploy](https://github.com/kratostaine/spring-authorization-server/actions/workflows/continuous-integration-workflow.yml/badge.svg)](https://github.com/kratostaine/spring-authorization-server/actions/workflows/continuous-integration-workflow.yml)
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
	![Apache](https://img.shields.io/badge/apache-%23D42029.svg?style=for-the-badge&logo=apache&logoColor=white)
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)



<h1 align="center"> HISTOBET-FEM </h1>

![image](https://github.com/Camilorod94/Proyecto-HISTOBET-FEM/assets/141589217/1f612e16-c696-4498-bba1-602f75778812)

### ¿Qué es? -
“HISTOBET-FEM” es una aplicación para los fanáticos del futbol profesional colombiano femenino y los que quieran conocer más sobre el mismo. La persona contará con un usuario y contraseña para acceder y seleccionar diferentes años entre el 2020 y el 2023, los cuales mostrarán en pantalla detalles de las finales de esos años seleccionados, así como el nombre de la goleadora y cantidad de goles anotados por la misma en ese año. Para esto usaremos Netbeans y modelo vista controlador (MVC). 


### Abstract –
"Historico BetPlay Femenino" is an application for fans of Colombian professional women's soccer and those who want to know more about it. The person will have a username and password for access with which they can access and select different years between 2000 and 2023, which will show details of the finals of those selected years on the screen, as well as the name of the scorer and amount of goals scored by it in that year. For this we will use Netbeans and a Model View Controller (MVC).


### Contenido: 
**_Historico_BetPlay_graficofin.ZIP_** = Ejecutables del aplicativo sin necesidad de Neatbens en .Jar, .Exe y .MSI.

**_Betplay01.zip_** = Primer avance del aplicativo. 

**_BetplayLigaFemenina_Grafico.jar_** = .Jar de la versión 2.0 del aplicativo. 

**_Historico_BetPlay_Listas1.ZIP_** = Primer avance del aplicativo implementando listas, sin entorno gráfico. 

**_Historico_BetPlay_graficofin.ZIP_** = Aplicativo final con entorno gráfico. 

**_IEEE Historico BetPlay.pdf_** = Primer avance formato IEE del aplicativo. 

**_Historico_BetPlay_Listas_Fin.ZIP** = Entrega final proyecto estructura, sin entorno gráfico. 



## I.	INTRODUCCIÓN
Este proyecto se realizará mediante el aplicativo Apache Netbens IDE 17, mediante arquitectura de modelo vista controlador (MVC), enfocando sus procesos en “Histórico BetPlay femenino”, que permitirá a sus usuarios tener la visualización del histórico de la Liga BetPlay - Futbol Femenino Colombiano durante los últimos 4 años, en cuanto a finales jugadas y estadísticas de las mismas. 


“Histórico BetPlay femenino” contará con un entorno gráfico que permitirá seleccionar diferentes opciones y funciones asociadas al año que el usuario seleccione como ejemplo: 

### 1. Acceso del usuario: 
Al iniciar la aplicación, el usuario visualizará una ventana en la que deberá acceder con su respectivo usuario y contraseña. El nombre de usuario será “ciclo3” y la contraseña de acceso será “proyecto”. Si los datos son correctos, podrá acceder al menú principal o en caso de ser errados, el sistema mostrará una alerta para que ingrese con los datos correctos. 

### 2. Menú principal: 
Luego de iniciar sesión, el usuario podrá visualizar el menú principal del aplicativo llamado "Histórico BetPlay Femenino". En el menú encontrará un listado de por lo menos 4 años descendiendo del 2023 a años anteriores.

### 3. Elección de año:
Al seleccionar uno de los años listados en pantalla, el usuario visualizará ahora en pantalla las estadísticas de las finales jugadas en el respectivo año, sea 2023, 2022, 2021 o 2020. Las estadísticas que aparecerán en pantalla de cada año son: Equipos finalistas, resultado de partido de ida, resultado de partido de vuelta, estadio en que se jugó cada partido, ganador de cada partido, nombre de la goleadora de ese año y cantidad de goles anotados por la misma. 

### 4. Botones: 
El aplicativo contendrá 2 botones, uno para finalizar el proceso o salir de la aplicación y otro dentro de cada año para retornar al menú principal para elegir otro año. 

Se podrá acceder fácilmente al histórico de finales de cada año seleccionado y retornar para elegir cualquier otro año sin problemas, de esta forma podrán recopilar ágilmente los datos del año que deseen, con un entorno gráfico amigable para cualquier usuario. 

## II. FUNCIONALIDAD.

1. Inicio de sesión:
   

   ![image](https://github.com/Camilorod94/Proyecto-HISTOBET-FEM/assets/141589217/fa859bd1-899a-4ab2-96cb-f85911a6772c)


3. Menú principal:
   
     ![image](https://github.com/Camilorod94/Proyecto-HISTOBET-FEM/assets/141589217/355060ac-835c-40b5-92e9-14a645cbc938)


4. Elección de un año:

  ![image](https://github.com/Camilorod94/Proyecto-HISTOBET-FEM/assets/141589217/e3957540-e2f4-4322-b806-5eca7057f091)


4. Créditos:
   
     ![image](https://github.com/Camilorod94/Proyecto-HISTOBET-FEM/assets/141589217/d44cd4af-ce7c-43a0-8c04-3e138e1bbc2f)

## III.	TECNOLOGÍAS UTILIZADAS.

**programa base:**

![image](https://github.com/Camilorod94/Proyecto-HISTOBET-FEM/assets/141589217/6a7ba4d8-a62b-4585-a8df-e4adb9810e71)

**Para el diagrama UML se ha utilizado:**

dia.exe 0.97.2 // Un programa para dibujar diagramas estructurados. // (C) 1998-2009 The Free Software Foundation and the authors

## IV. CONCLUSIONES:

Por medio de este proyecto he ampliado mis conocimientos en cuanto a Modelo Vista Controlador y entorno gráfico mediante Java Netbeans. Por lo que ya soy capaz de implementar entornos gráficos a proyectos y códigos generados, además de poder agregar listas y tablas.

Se implementó procesos de ciclos anteriores con diversas clases, con herencia polimorfismo y demás, pero ahora unificando todo con un menú y su respectivo entorno gráfico. 

Ahora soy capaz de generar un inicio de sesión con usuario y contraseña, así como alertas de contraseña errónea. 

Desde la realización del proyecto, puedo crear contenedores para la distribución visual de elementos dentro de una ventana, además de generar color y modificación en los mismos. 

He logrado mejorar en gran medida mis habilidades generales de programación y conocer más sobre Java y Neatbens así como de sus respectivos componentes.



## V.	CRÉDITOS.

![image](https://github.com/Camilorod94/Proyecto-HISTOBET-FEM/assets/141589217/4e120e49-5107-469a-8649-110b97cd584d)
 

Cristian Camilo De Los Rios Rodríguez. 
Cristian.de.los.rios@pi.edi.co

Me gustan los video juegos, las películas, escuchar música y viajar por carretera. 

Actualmente en proceso como tecnólogo de desarrollo, espero ser un excelente programador a futuro y poner en práctica todo lo aprendido en el transcurso de estos ciclos. 
