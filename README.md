# Liga_BetPlay
Proyecto Politécnico Internacional. Liga BetPlay (En desarrollo).


Resumen - “Histórico BetPlay femenino” es una aplicación para los fanáticos del futbol profesional colombiano femenino y los que quieran conocer más sobre el mismo. La persona contará con un usuario y contraseña para el acceso con la que podrá acceder y seleccionar diferentes años entre el 2000 y el 2023, los cuales mostrarán en pantalla detalles de las finales de esos años seleccionados, así como el nombre de la goleadora y cantidad de goles anotados por la misma en ese año. Para esto usaremos Netbeans y modelo vista controlador (MVC). 

Palabras clave: Modelo Vista controlador (MVC), Pilares de la POO, Entorno gráfico. 

    Abstract – "Historico BetPlay Femenino" is an application for fans of Colombian professional women's soccer and those who want to know more about it. The person will have a username and password for access with which they can access and select different years between 2000 and 2023, which will show details of the finals of those selected years on the screen, as well as the name of the scorer and amount of goals scored by it in that year. For this we will use Netbeans and a Model View Controller (MVC).

Keywords: Model View Controller (MVC), OOP Pillars, Graphical environment.
I.	INTRODUCCIÓN
Este proyecto se realizará mediante el aplicativo Apache Netbens IDE 17, mediante arquitectura de modelo vista controlador (MVC), enfocando sus procesos en “Histórico BetPlay femenino”, que permitirá a sus usuarios tener la visualización del histórico de la Liga BetPlay - Futbol Femenino Colombiano durante los últimos 4 años, en cuanto a finales jugadas y estadísticas de las mismas. 




“Histórico BetPlay femenino” contará con un entorno gráfico que permitirá seleccionar diferentes opciones y funciones asociadas al año que el usuario seleccione como ejemplo: 



1. Acceso del usuario: 
Al iniciar la aplicación, el usuario visualizará una ventana en la que deberá acceder con su respectivo usuario y contraseña. El nombre de usuario será “ciclo3” y la contraseña de acceso será “proyecto”. Si los datos son correctos, podrá acceder al menú principal o en caso de ser errados, el sistema mostrará una alerta para que ingrese con los datos correctos. 

2. Menú principal: 
Luego de iniciar sesión, el usuario podrá visualizar el menú principal del aplicativo llamado "Histórico BetPlay Femenino". En el menú encontrará un listado de por lo menos 4 años descendiendo del 2023 a años anteriores.

3. Elección de año:
Al seleccionar uno de los años listados en pantalla, el usuario visualizará ahora en pantalla las estadísticas de las finales jugadas en el respectivo año, sea 2023, 2022, 2021 o 2020. Las estadísticas que aparecerán en pantalla de cada año son: Equipos finalistas, resultado de partido de ida, resultado de partido de vuelta, estadio en que se jugó cada partido, ganador de cada partido, nombre de la goleadora de ese año y cantidad de goles anotados por la misma. 

4. Botones: 
El aplicativo contendrá 2 botones, uno para finalizar el proceso o salir de la aplicación y otro dentro de cada año para retornar al menú principal para elegir otro año. 

Se podrá acceder fácilmente al histórico de finales de cada año seleccionado y retornar para elegir cualquier otro año sin problemas, de esta forma podrán recopilar ágilmente los datos del año que deseen, con un entorno gráfico amigable para cualquier usuario. 
II.	CÓDIGO DE HISTORICO BETPLAY FEMENINO.

Código comentado para su fácil entendimiento, además de un comentario al inicio de cada clase para mayor comprensión. 

1. Se importan las librerías a utilizar. 

import java.util.Scanner;
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

2. Se crea el Main que básicamente funciona para llamar la “ventanainiciodesesion”. Que es el método para el acceso del usuario y contraseña. 

public class BetplayLigaFemenina_Grafico {

    public static void main(String[] args) {
        // Crear una ventana de inicio de sesión
        SwingUtilities.invokeLater(() -> {
            VentanaInicioSesion ventanaInicioSesion = new VentanaInicioSesion();
            ventanaInicioSesion.setVisible(true);
        });
    }
}


3. Se crea la superclase “Anio”, que llamará los métodos de los demás años y especificará los datos de las finales de cada año. 

package betplayligafemenina_grafico;

public abstract class Anio {
    // Atributos privados para almacenar los detalles del año
    private int anio; // El año del torneo
    private Equipo equipoCampeon; // El equipo campeón del torneo en ese año
    private Equipo equipoSubcampeon; // El equipo subcampeón del torneo en ese año
    private Final finalPartidoIda; // Los detalles del partido de ida de la final en ese año
    private Final finalPartidoVuelta; // Los detalles del partido de vuelta de la final en ese año
    private Jugadora goleadora; // La jugadora goleadora del torneo en ese año

    // Constructor para crear un objeto de tipo Anio con los detalles proporcionados
    public Anio(int anio, Equipo equipoCampeon, Equipo equipoSubcampeon, Final finalPartidoIda, Final finalPartidoVuelta, Jugadora goleadora) {
        this.anio = anio; // Inicializar el año con el valor proporcionado
        this.equipoCampeon = equipoCampeon; // Inicializar el equipo campeón con el valor proporcionado
        this.equipoSubcampeon = equipoSubcampeon; // Inicializar el equipo subcampeón con el valor proporcionado
        this.finalPartidoIda = finalPartidoIda; // Inicializar los detalles del partido de ida con el valor proporcionado
        this.finalPartidoVuelta = finalPartidoVuelta; // Inicializar los detalles del partido de vuelta con el valor proporcionado
        this.goleadora = goleadora; // Inicializar la jugadora goleadora con el valor proporcionado
    }

    // Método abstracto que debe ser implementado en las subclases para obtener información detallada sobre el año
    public abstract String obtenerInfoAnio();

    // Métodos para acceder a los detalles del año
    public int getAnio() {
        return anio;
    }

    public Equipo getEquipoCampeon() {
        return equipoCampeon;
    }

    public Equipo getEquipoSubcampeon() {
        return equipoSubcampeon;
    }

    public Final getFinalPartidoIda() {
        return finalPartidoIda;
    }

    public Final getFinalPartidoVuelta() {
        return finalPartidoVuelta;
    }

    public Jugadora getGoleadora() {
        return goleadora;
    }

    // Sobrescribir el método toString para obtener información del año al convertir el objeto a cadena de texto
    @Override
    public String toString() {
        return obtenerInfoAnio();
    }
}

4. Se crea la clase “Anio2020” y otras clases con “Anio2021, 2022 y 2023” en la cual se ingresan los datos de las finales de cada año. Se crean métodos “obtenerInfoAnio” para que pueda ser llamado desde otra clase. Clases Anio, extends Anio.

public class Anio2020 extends Anio {
    
    // Constructor de la subclase Anio2020
    public Anio2020() {
        // Llamada al constructor de la clase base (Anio) para crear un objeto Anio2020 con detalles específicos del año 2020
        super(
            2020, // Año
            new Equipo("Santa Fe"), // Equipo campeón
            new Equipo("América de Cali"), // Equipo subcampeón
            new Final(
                new Equipo("América de Cali"), // Equipo local
                new Equipo("Santa Fe"), // Equipo visitante
                1, 2, // Resultado ida
                "Estadio Pascual Guerrero, Cali", // Lugar ida
                "América de Cali" // Equipo ganador ida
            ),
            new Final(
                new Equipo("Santa Fe"), // Equipo local
                new Equipo("América de Cali"), // Equipo visitante
                2, 0, // Resultado vuelta
                "Estadio El Campín, Bogotá", // Lugar vuelta
                "Santa Fe" // Equipo ganador vuelta
            ),
            new Jugadora("Ysaura Viso", 13) // Goleadora del año 2020
        );
    }

    // Implementación del método abstracto obtenerInfoAnio() para mostrar información detallada del año 2020
    @Override
    public String obtenerInfoAnio() {
        // Crear una cadena con la información detallada del año 2020
        return "Año 2020:\n" +
            "Campeón: " + getEquipoCampeon().getNombre() + "\n" +// Obtener información detallada del campeón
            "Subcampeón: " + getEquipoSubcampeon().getNombre() + "\n" + // Obtener información detallada del subcampeón
            "Goleadora: " + getGoleadora().getNombre() + " (" + getGoleadora().getGoles() + " goles)\n" +// Obtener información detallada del nombre y goles de la goleadora
            "Detalles del partido ida:\n" +
            getFinalPartidoIda().obtenerInfo() + "\n" + // Obtener información detallada del partido de ida
            "Detalles del partido vuelta:\n" +
            getFinalPartidoVuelta().obtenerInfo(); // Obtener información detallada del partido de vuelta
    }
}



5. Se crea la clase Equipo que se encargará de crear el método para obtener el nombre de los equipos. 

public class Equipo {
    private String nombre;

    // Constructor que recibe el nombre del equipo
    public Equipo(String nombre) {
        this.nombre = nombre;
    }

    // Método para obtener el nombre del equipo
    public String getNombre() {
        return nombre;
    }
}




6. Se crea la clase “Final”, que representa los detalles de los partidos de la final en el año que sea solicitado. 

public class Final {
    private Equipo equipoLocal;
    private Equipo equipoVisitante;
    private int golesEquipoLocal;
    private int golesEquipoVisitante;
    private String estadio;
    private String ganador;

    // Constructor que recibe los detalles del partido final
    public Final(Equipo equipoLocal, Equipo equipoVisitante, int golesEquipoLocal, int golesEquipoVisitante, String estadio, String ganador) {
        this.equipoLocal = equipoLocal;
        this.equipoVisitante = equipoVisitante;
        this.golesEquipoLocal = golesEquipoLocal;
        this.golesEquipoVisitante = golesEquipoVisitante;
        this.estadio = estadio;
        this.ganador = ganador;
    }

    // Métodos para obtener los detalles del partido final
    public Equipo getEquipoLocal() {
        return equipoLocal;
    }

    public Equipo getEquipoVisitante() {
        return equipoVisitante;
    }

    public int getGolesEquipoLocal() {
        return golesEquipoLocal;
    }

    public int getGolesEquipoVisitante() {
        return golesEquipoVisitante;
    }

    public String getEstadio() {
        return estadio;
    }

    public String getGanador() {
        return ganador;
    }

    // Método para obtener una cadena de información detallada sobre el partido final
    public String obtenerInfo() {
        return "Equipo Local: " + equipoLocal.getNombre() + "\n" +
               "Equipo Visitante: " + equipoVisitante.getNombre() + "\n" +
               "Goles Equipo Local: " + golesEquipoLocal + "\n" +
               "Goles Equipo Visitante: " + golesEquipoVisitante + "\n" +
               "Estadio: " + estadio + "\n" +
               "Ganador: " + ganador + "\n";
    }
}


7. Se crea la clase “Jugadora” que contendrá el método para llamar por el nombre de la jugadora y la cantidad de goles anotados, según el año seleccionado. 

public class Jugadora {
    private String nombre;
    private int goles;

    // Constructor que recibe el nombre de la jugadora y la cantidad de goles
    public Jugadora(String nombre, int goles) {
        this.nombre = nombre;
        this.goles = goles;
    }

    // Método para obtener el nombre de la jugadora
    public String getNombre() {
        return nombre;
    }

    // Método para obtener la cantidad de goles que ha marcado la jugadora
    public int getGoles() {
        return goles;
    }
}


8.Se crea clase “VentanaInformacionAnio”, la cual se encarga de generar un entorno gráfico en una ventana emergente que muestra la información de el año solicitado. Adicional, se configura su presentación como tamaño de la ventana, titulo de la ventana, botón para “salir” y botón para “regresar”. 

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class VentanaInformacionAnio extends JFrame {

    // Constructor de la clase que recibe el título de la ventana y la información del año
    public VentanaInformacionAnio(String tituloVentana, String informacionAnio) {
        super(tituloVentana); // Llama al constructor con el título proporcionado
        setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE); // Configura el cierre de la ventana al cerrar esta ventana (sin salir de la aplicación), por defecto con el de minimizar y ampliar
        setSize(600, 400); // Establece el tamaño de la ventana a 600x400 píxeles
        setLocationRelativeTo(null); // Centra la ventana en la pantalla

        // Crea un área de texto editable que muestra la información del año
        JTextArea textoInformacion = new JTextArea(informacionAnio);
        textoInformacion.setEditable(false); // Desactiva la edición del texto
        JScrollPane scrollPane = new JScrollPane(textoInformacion); // Agrega un panel de desplazamiento si es necesario, al ser pocos campos no se usa.

        // Crea un botón "Volver" para cerrar esta ventana y volver a la ventana anterior
        JButton botonAtras = new JButton("Volver");
        botonAtras.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                dispose(); // Cierra la ventana actual
            }
        });

        // Crea un botón "Salir" para cerrar toda la aplicación
        JButton botonSalir = new JButton("Salir");
        botonSalir.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                System.exit(0); // Sale de la aplicación
            }
        });

        // Crea un panel para colocar los botones "Volver" y "Salir" uno al lado del otro
        JPanel panelBotones = new JPanel();
        panelBotones.setLayout(new GridLayout(1, 2)); // Usar un GridLayout para los botones
        panelBotones.add(botonAtras); // Agrega el botón "Volver"
        panelBotones.add(botonSalir); // Agrega el botón "Salir"

        // Configura el diseño de la ventana principal con un BorderLayout
        Container container = getContentPane();
        container.setLayout(new BorderLayout());

        // Agrega el área de texto en el centro y el panel de botones en la parte inferior
        container.add(scrollPane, BorderLayout.CENTER);
        container.add(panelBotones, BorderLayout.SOUTH);
    }
}

9. Se crea la clase “VentanaInicioSesion” que es la que contendrá los JLabel, JTextField, JPasswordField y JButton, para el menú o pantalla de inicio de sesión del usuario, en el cual el usuario será: ciclo3 y la contraseña: proyecto.
Adicional, se crean métodos para la apariencia de la ventana y espacio entre botones. 

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class VentanaInicioSesion extends JFrame {

    private JLabel labelUsuario, labelContrasena, labelMensaje;
    private JTextField campoUsuario;
    private JPasswordField campoContrasena;
    private JButton botonIniciarSesion;
    private JButton botonSalir;

    public VentanaInicioSesion() {
        setTitle("Histórico Liga BetPlay Femenina");
        setSize(400, 250);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);
        setResizable(false);

        JPanel panel = new JPanel();
        panel.setLayout(new GridBagLayout());

        GridBagConstraints gbc = new GridBagConstraints();
        gbc.insets = new Insets(20, 5, 5, 5); // Aumentado el valor del margen superior

        // Agregar el título centrado en la parte superior
        labelMensaje = new JLabel("  Inicia sesión para acceder a historico BetPlay Femenino");
        labelMensaje.setHorizontalAlignment(JLabel.CENTER);
        gbc.gridx = 0;
        gbc.gridy = 0;
        gbc.gridwidth = 2;
        panel.add(labelMensaje, gbc);

        labelUsuario = new JLabel("ciclo3");
        campoUsuario = new JTextField("Ejemplo123");
        labelContrasena = new JLabel("Contraseña:");
        campoContrasena = new JPasswordField("proyecto");
        botonIniciarSesion = new JButton("Acceder");
        botonSalir = new JButton("Salir");

        gbc.gridwidth = 1;

        gbc.gridy = 1;
        panel.add(labelUsuario, gbc);
        gbc.gridx = 1;
        panel.add(campoUsuario, gbc);

        gbc.gridy = 2;
        gbc.gridx = 0;
        panel.add(labelContrasena, gbc);
        gbc.gridx = 1;
        panel.add(campoContrasena, gbc);

        gbc.gridy = 3;
        gbc.gridx = 0;
        panel.add(botonSalir, gbc);
        gbc.gridx = 1;
        panel.add(botonIniciarSesion, gbc);
        

        botonIniciarSesion.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String usuario = campoUsuario.getText();
                char[] contrasena = campoContrasena.getPassword();
                String contrasenaStr = new String(contrasena);

                if (usuario.equals("ciclo3") && contrasenaStr.equals("proyecto")) {
                    dispose(); // Cierra la ventana de inicio de sesión
                    VentanaMenu ventanaMenu = new VentanaMenu();
                    ventanaMenu.setVisible(true); // Abre la ventana del menú
                } else {
                    JOptionPane.showMessageDialog(null, "Usuario o contraseña incorrectos", "Error de inicio de sesión", JOptionPane.ERROR_MESSAGE);// Genera mensaje emergente de error
                }
            }
        });

        botonSalir.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                System.exit(0); // Salir de la aplicación al hacer clic en "Salir"
            }
        });

        add(panel);
    }
}


10. Se crea la clase: “VentanaMenu”, que será el entorno gráfico donde se encontrará el menú con los años “botones” a seleccionar. Estos botones de cada año estarán asociados al método “mostrarVentanaInformacionAnio” para que al hacer clic en ellos, se abra la ventana emergente con la información correspondiente a cada año. Se usa el JFrame para la ventana emergente de cada año.  

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class VentanaMenu extends JFrame {

    public VentanaMenu() {
        setTitle("Histórico BetPlay Femenino"); // Título de la ventana
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(500, 400); // Tamaño de la ventana
        setLocationRelativeTo(null); // Centrar la ventana en la pantalla

        JPanel panelBotones = new JPanel();
        panelBotones.setLayout(new BoxLayout(panelBotones, BoxLayout.Y_AXIS)); // Usar BoxLayout vertical
        panelBotones.setAlignmentX(Component.CENTER_ALIGNMENT); // Centrar los componentes horizontalmente

        // Agregar el nuevo título dentro del cuerpo de la ventana
        
        JLabel titulo = new JLabel("Bienvenido al Histórico BetPlay Femenino");
        titulo.setFont(new Font("Arial", Font.BOLD, 18)); // Establecer el tipo de fuente y tamaño del título
        titulo.setAlignmentX(Component.CENTER_ALIGNMENT); // Centrar el título horizontalmente
        titulo.setForeground(Color.BLUE); // Cambiar el color del texto
        
        
        
        

        // Agregar el mensaje "Elija el año del cual desea saber los detalles de la final"
        JLabel mensaje = new JLabel("Elija el año del cual desea saber los detalles de la final");
        mensaje.setAlignmentX(Component.CENTER_ALIGNMENT); // Centrar el mensaje horizontalmente
        mensaje.setFont(new Font("Arial", Font.BOLD, 14)); // Establecer el tipo de fuente y tamaño del mensaje
        mensaje.setForeground(Color.black); // Color del texto

        // Crear botones
        JButton botonAnio2020 = new JButton("Año 2020");
        JButton botonAnio2021 = new JButton("Año 2021");
        JButton botonAnio2022 = new JButton("Año 2022");
        JButton botonAnio2023 = new JButton("Año 2023");
        JButton botonSalir = new JButton("Salir");

        // Ajustar el tamaño de los botones en la ventana
        Dimension buttonSize = new Dimension(300, 100);
        botonAnio2020.setPreferredSize(buttonSize);
        botonAnio2021.setPreferredSize(buttonSize);
        botonAnio2022.setPreferredSize(buttonSize);
        botonAnio2023.setPreferredSize(buttonSize);
        botonSalir.setPreferredSize(buttonSize);

        botonAnio2020.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                Anio2020 anio2020 = new Anio2020();
                mostrarVentanaInformacionAnio(anio2020);
            }
        });

        botonAnio2021.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                Anio2021 anio2021 = new Anio2021();
                mostrarVentanaInformacionAnio(anio2021);
            }
        });

        botonAnio2022.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                Anio2022 anio2022 = new Anio2022();
                mostrarVentanaInformacionAnio(anio2022);
            }
        });

        botonAnio2023.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                Anio2023 anio2023 = new Anio2023();
                mostrarVentanaInformacionAnio(anio2023);
            }
        });

        botonSalir.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                System.exit(0);
            }
        });

        // Agregar el mensaje y botones al panel de botones
        panelBotones.add(titulo); // Agregar el título al panel de botones
        panelBotones.add(Box.createRigidArea(new Dimension(0, 20))); // Espacio vertical antes del mensaje
        panelBotones.add(mensaje);
        panelBotones.add(Box.createRigidArea(new Dimension(0, 20))); // Espacio vertical entre el mensaje y los botones
        panelBotones.add(botonAnio2020);
        panelBotones.add(Box.createRigidArea(new Dimension(0, 10))); // Espacio vertical entre botones
        panelBotones.add(botonAnio2021);
        panelBotones.add(Box.createRigidArea(new Dimension(0, 10)));
        panelBotones.add(botonAnio2022);
        panelBotones.add(Box.createRigidArea(new Dimension(0, 10)));
        panelBotones.add(botonAnio2023);
        panelBotones.add(Box.createRigidArea(new Dimension(0, 25))); // Espacio vertical entre los botones y el borde inferior
        panelBotones.add(botonSalir);
        

        Container container = getContentPane();
        container.setLayout(new BorderLayout());
        container.add(panelBotones, BorderLayout.CENTER); // Centrar el panel de botones en la ventana

        setVisible(true);
    }

    private void mostrarVentanaInformacionAnio(Anio anio) {
        VentanaInformacionAnio ventanaInformacionAnio = new VentanaInformacionAnio("Información del Año", anio.obtenerInfoAnio());
        ventanaInformacionAnio.setVisible(true);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new VentanaMenu();
            }
        });
    }
}
III.	DIAGRAMA UML

 


IV.	DICCIONARIO DE DATOS

Diccionario de datos
Nombre	Tipo de dato	Descripción
Scanner	Scanner	Para leer el dato ingresado por el usuario
opcion	Int 	Entero para las opciones del menú
do	do	Ciclo para el menú
opcion	switch	Crea el menú
opcion	while	Cierra el ciclo del menú
nombre	String	Nombre del equipo
nombre	String	Nombre de la goleadora
goles	Int 	Cantidad de goles de la goleadora
golesLocal	Int 	Cantidad de goles anotados por el equipo local en la final
golesVisitante	Int 	Cantidad de goles anotados por el equipo visitante en la final
estadio	String	Estadio donde se jugó la final
ganador	String	Equipo que ganó la final
anio	Int 	Represente el año en el que se jugó la final 
Equipo	clase	Representa un equipo participante en la final del torneo.
Jugadora	clase	Representa una jugadora destacada en el torneo, con nombre y cantidad de goles.
Final	clase	Representa los detalles de una final, incluyendo los equipos participantes, los resultados de los partidos de ida y vuelta, el lugar y el equipo ganador.
obtenerInfoAnio	Método	Método abstracto en la clase "Anio" que devuelve una cadena con información detallada del año.
obtenerInfo	Método	Método en la clase "Final" que devuelve una cadena con información detallada sobre una final.
BetPlayLigaFemenina	Clase (principal)	Representa el punto de entrada de la aplicación y contiene el bucle principal para mostrar el menú de años y detalles.
mostrarInfoAnio	Método	Método en la clase "BetPlayLigaFemenina" que muestra información detallada sobre un año específico.
VentanaInformacionAnio	clase	Ventana del entorno gráfico en donde es llamado el detalle de cada año. 
textoInformacion	JTextArea	Espacio para ingresar texto
scrollPane	JScrollPane	Panel para deslizar de ser necesario
botonSalir	JButton	Botón para salir del aplicativo
panelBotones	JPanel	Contenedor para seccionar el menú.
Container	container	Genera espacios no visibles para seccionar en cuadriculas o dividir el menú
javax.swing.*	Biblioteca	Biblioteca de entorno gráfico
labelUsuario	JLabel	Campo de texto predefinido para que se visualice “Usuario”
campoUsuario	JTextField	Para que el usuario ingrese su “usuario”. 
labelContrasena	JLabel	Campo predefinido para que se visualice la palabra “Contraseña”. 
campoContrasena	JPasswordField	Espacio para ingresar la contraseña
botonIniciarSesion	JButton	Botón de inicio de sesión
gbc	GridBagConstraints	Cuadriculas dentro del panel. 
contrasenaStr	String	Recibe la contraseña ingresada
contrasena	char	Muestra asteriscos en el campo de contraseña
setTitle	setTitle	Define un titulo 
panelBotones	JPanel	Crea un panel para ajustar allí los botones
titulo	JLabel	Predefine un titulo para la sección de menú
mensaje	JLabel	Muestra un mensaje de bienvenida en el menú. 
botonAnio2020	JButton	Botón para el año 2020, se crea uno para cada año, hasta el 2023.
Dimension	buttonSize	Se generan dimensiones para los botones

V.	MOCKUPS.
 
 
 
 
VI.	CONCEPTOS DE LA POO Y MVC.

POLIMORFISMO: Permite que diferentes clases se comporten de manera similar mediante la implementación de métodos en común. Con esto se puede reutilizar el código y genera flexibilidad en el mismo. 

En este proyecto, un ejemplo claro de polimorfismo se encuentra en la implementación del método obtenerInfoAnio() en cada una de las subclases Anio2020, Anio2021, Anio2022 y Anio2023. Aunque estos métodos están definidos en la clase abstracta Anio, cada subclase los implementa de manera específica para mostrar la información detallada de cada año en el torneo. Sin embargo, desde el punto de vista del método mostrarInfoAnio en el BetPlayLigaFemenina, se puede llamar al método obtenerInfoAnio() en cualquier objeto de tipo Anio, independientemente de su subclase, lo que demuestra el polimorfismo.

ABSTRACCIÓN: Consiste en simplificar y representar objetos del mundo real en modelos concretos y manejables en el código. En esencia, la abstracción implica centrarse en los aspectos esenciales de un objeto y ocultar los detalles innecesarios para lograr una representación más clara y eficiente.

La clase abstracta Anio es un ejemplo de abstracción, ya que encapsula los detalles generales de cada año en el torneo, como el equipo campeón, el equipo subcampeón, los detalles de las finales y la jugadora goleadora. Aunque cada año tiene detalles únicos, la clase Anio proporciona una representación abstracta de estos detalles comunes.

HERENCIA: permite crear nuevas clases basadas en clases existentes, compartiendo sus atributos y métodos, extendiendo o modificando su comportamiento según requiera. Las clases derivadas heredan las características de la clase base, lo que promueve la reutilización de código y la organización por jerarquía de objetos.

En miz proyecto, la herencia se encuentra en la relación entre las clases base y las subclases que extienden sus características. Ejemplos de herencia en tu proyecto son:

La clase Anio es una clase base abstracta que proporciona una estructura general para representar un año en el torneo. Las subclases como Anio2020, Anio2021, Anio2022 y Anio2023 heredan de Anio y extienden su funcionalidad específica para cada año.

ENCAPSULAMIENTO: Permite definir los atributos y métodos de una clase de manera que solo puedan ser accedidos y modificados de acuerdo con las reglas establecidas por la clase, protegiendo así la integridad y la consistencia de los datos.

En mi proyecto, el encapsulamiento se encuentra en la definición de las clases y en cómo se controla el acceso a los atributos y métodos de estas clases. Aquí hay algunos ejemplos de encapsulamiento en tu proyecto:

En la clase Equipo, los atributos son privados, lo que significa que solo pueden ser accedidos y modificados desde dentro de la clase. El encapsulamiento aszegura que estos atributos solo sean modificados de acuerdo con la lógica interna de la clase, evitando modificaciones no deseadas y garantizando la consistencia de los datos.

En la clase Jugadora, los atributos nombre, goles y equipo son privados, lo que significa que solo pueden ser accedidos y modificados mediante métodos públicos definidos en la misma clase. Esto controla el acceso a la información de las jugadoras y permite establecer reglas para la asignación de goles y la asociación con un equipo.

MODELO VISTA CONTROLADOR: MVC es un acrónimo que significa Modelo-Vista-Controlador. Es usado para separar y organizar el código en tres componentes principales, lo que facilita la gestión y mantenimiento de las aplicaciones.

Modelo: Representa los datos y la lógica de la aplicación. Contiene la estructura de datos, la lógica para acceder y manipular dichos datos. 

Vista: Presenta los datos al usuario y a su vez la interfaz. Representa cómo se visualiza y se interactúa con los datos. 

Controlador: Es el intermediario entre el modelo y la vista. Procesa las solicitudes del usuario desde la vista, interactúa con el modelo para obtener o actualizar los datos, y actualiza la vista con los resultados.

Cada uno de estos componentes se centra en tareas especificas para facilitar la comprensión, el mantenimiento y las actualizaciones del código. 
Ya que todo está separado, favorece la re utilización del código en diferentes partes de la aplicación.  Adicional los componentes, al estar separados, son más fáciles de probar y esto mejora enormemente la calidad del Software. 

Se puede trabajar desde diferentes equipos de trabajo a la vez en diferentes partes del código, sin afectar los avances de los otros colaboradores. 




LISTA ABSTRACTA: Estas encapsulan operaciones de las listas para simplificar su implementación. Define el comportamiento de una estructura de datos sin detallar su implementación. Esto ayuda a la modularidad y la reutilización del código.

CLASE INTERNA DE ENLACE: Las clases internas son 
clases anidadas dentro de otras clases o métodos, que conectan a su vez con otra clase o subclase. Se caracteriza por su eficiencia en la inserción y eliminación de datos.

LISTA GENERICA: Una lista es genérica cuando se pueden insertar o extraer datos de cualquier parte de la lista. Pueden manejar datos variables evitando así la redundancia en la implementación de estructuras de datos.

En nuestro proyecto, la podemos encontrar en: 

 

LISTA TIPADA: Estas restringen la lista a un tipo de dato especifico como lo puede ser, cadena de texto, entero, Booleano o demás, lo que previene error en los mismos durante la compilación. Con lo anterior, se asegura que solo los elementos compatibles sean almacenados en las listas, generando confiabilidad y el fácil mantenimiento del código. 

En nuestro código se encuentra en:

 


LISTA DE POSICIÓN ORDINAL: Esta permite llevar un seguimiento ordenado de los elementos de la lista, numerándolos desde el inicio hasta el final de la misma. Es ideal para realizar Rankings, histórico de transacciones o registro de actividades. 

En nuestro proyecto la podemos encontrar en:
 

MÉTOODO DE INTERACCIÓN: Esta permite recorrer y manipular las colecciones de datos de manera eficiente y entendible. Pueden ayudar en la simplificación de tareas como filtrar datos, lo que reduce la necesidad de bucles. métodos, como "forEach" y "map", mejoran la mantenibilidad y comprensión del código, al tiempo que promueven la escritura de programas más eficientes y funcionales.

PILA: Son implementadas para mantener el flujo de ejecución en la programación. Se mantiene mediante las operaciones “push” para agregar datos y “pop” para retirar los mismos y que el mismo sistema los clasifique ordenadamente lo que permite controlar y gestionar estados. En esta se mantiene el proceso que el ultimo dato en entrar, es el primero en salir. 


JTABLE: Este es un componente visual de Java que nos permite dibujar una tabla, de forma que en cada fila/columna de la tabla podamos poner el dato que queramos; un nombre, un apellido, una edad, un número, etc.

JLIST: Es un componente de Java que permite que permite seleccionar uno o más elementos de una lista, o un grupo de elementos para elegir.

JPROGRESSBAR: Esta se usa para mostrar visualmente una barra de carga, indicando el tiempo que puede tardar en completarse una tarea. 

JTREE: Es un componente visual de Java que permite ordenar algunos datos jerárquicamente o como “árbol”, permitiendo seleccionar un elemento el cual desplegará en carpetas internas nuevos elementos que este esté conteniendo. 

SETTITLE: Este permite asignar un título a nuestro Jframe o pantalla visual en la que nos encontremos actualmente, en nuestro proyecto podemos encontrarlo en los encabezados de cada ventana, por ejemplo: 

 
 

JCOMBOBOX: También se conoce como lista desplegable, es un componente de combinación entre botón y una lista desplegable.  

JBUTTON: Es un componente de Java que funciona como “botón” y permite llevar a otra parte del código. 

En este código se utiliza para realizar la creación de los botones “Acceder”, ”Salir”, “Atrás” y el correspondiente a cada uno de los años en el “menú”, por ejemplo: 

 

JFRAME: Es una clase utilizada por la biblioteca Swing (gráfica) para generar nuevas ventanas emergentes sobre las cuales el usuario puede o no interactuar, además posee por defecto las opciones de ampliar, minimizar o cerrar. 

JLABEL: Este permite ingresar un texto estático en un panel, para que sea mostrada en pantalla, esta información no puede variar, también se puede usar para mostrar en pantalla algunos resultados.  

En nuestro proyecto se utiliza para crear textos en el entorno gráfico, en este caso predefinidos, como por ejemplo, el texto de “Usuario”, “Contraseña”, el mensaje de bienvenida, o el que informa que se debe iniciar sesión para acceder al histórico, en la ventana de inicio de sesión y en las demás: 
 


 

JTEXTFIELD: Se utiliza para crear un cuadro de texto en el que el usuario puede ingresar información, la cual se puede almacenar, comparar o simplemente visualizar en pantalla.
En este proyecto se implementa en la sección de “Usuario”, en donde se solicita el ingreso por teclado del “Usuario” para compararlo con el almacenado, esto en la ventana de “inicio de sesión”. 
 

JSCROLLPANE: Se utiliza para crear una barra de desplazamiento en el entorno gráfico en caso de ser necesaria. En nuestro proyecto es implementada, pero por la poca cantidad de datos, no se logra visualizar en pantalla.
 
VII.	TECNOLOGÍAS UTILIZADAS.

Este proyecto fue desarrollado en: 

Product Version: Apache NetBeans IDE 17
Updates: Updates available
Java: 15.0.2; Java HotSpot(TM) 64-Bit Server VM 15.0.2+7-27
Runtime: Java(TM) SE Runtime Environment 15.0.2+7-27
System: Windows 10 version 10.0 running on amd64; Cp1252; es_CO (nb)

Para el diagrama se ha utilizado: 

dia.exe 0.97.2 // Un programa para dibujar diagramas estructurados. // (C) 1998-2009 The Free Software Foundation and the authors


VIII.	REFERENCIAS.


Colaboradores de los proyectos Wikimedia. "Liga Profesional Femenina de Fútbol 2020 (Colombia) - Wikipedia, la enciclopedia libre". Wikipedia, la enciclopedia libre. https://es.wikipedia.org/wiki/Liga_Profesional_Femenina_de_Fútbol_2020_(Colombia) (accedido el 15 de agosto de 2023).

Colaboradores de los proyectos Wikimedia. "Liga Profesional Femenina de Fútbol 2021 (Colombia) - Wikipedia, la enciclopedia libre". Wikipedia, la enciclopedia libre. https://es.wikipedia.org/wiki/Liga_Profesional_Femenina_de_Fútbol_2021_(Colombia) (accedido el 15 de agosto de 2023).

Colaboradores de los proyectos Wikimedia. "Liga Profesional Femenina de Fútbol 2022 (Colombia) - Wikipedia, la enciclopedia libre". Wikipedia, la enciclopedia libre. https://es.wikipedia.org/wiki/Liga_Profesional_Femenina_de_Fútbol_2022_(Colombia) (accedido el 15 de agosto de 2023).

Colaboradores de los proyectos Wikimedia. "Liga Profesional Femenina de Fútbol 2023 (Colombia) - Wikipedia, la enciclopedia libre". Wikipedia, la enciclopedia libre. https://es.wikipedia.org/wiki/Liga_Profesional_Femenina_de_Fútbol_2023_(Colombia) (accedido el 15 de agosto de 2023).

Harol. (s. f.). GitHub - Harol003/Java_Estructura_Datos: Java_Estructura_Datos. GitHub. https://github.com/Harol003/Java_Estructura_Datos

ABCdatos.com. (s. f.). Ejemplo de uso de un JTable con un TableModel en Java. https://www.abcdatos.com/tutoriales/tutorial/z3128.html

ABCdatos.com. (s. f.). Ejemplo de uso de un JTable con un TableModel en Java. https://www.abcdatos.com/tutoriales/tutorial/z3128.html

colaboradores de Wikipedia. (2022). Jframe. Wikipedia, la enciclopedia libre. https://es.wikipedia.org/wiki/Jframe

Jlabel en java. (2018, 16 abril). PROGRAMACION. https://victomanolo.wordpress.com/jlabel-en-java/
