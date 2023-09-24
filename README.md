![Badge en Desarollo](https://img.shields.io/badge/STATUS-EN%20DESAROLLO-green)



<h1 align="center"> HISTOBET-FEM </h1>




### Resumen -
“HISTOBET-FEM” es una aplicación para los fanáticos del futbol profesional colombiano femenino y los que quieran conocer más sobre el mismo. La persona contará con un usuario y contraseña para el acceso con la que podrá acceder y seleccionar diferentes años entre el 2000 y el 2023, los cuales mostrarán en pantalla detalles de las finales de esos años seleccionados, así como el nombre de la goleadora y cantidad de goles anotados por la misma en ese año. Para esto usaremos Netbeans y modelo vista controlador (MVC). 



### Abstract –
"Historico BetPlay Femenino" is an application for fans of Colombian professional women's soccer and those who want to know more about it. The person will have a username and password for access with which they can access and select different years between 2000 and 2023, which will show details of the finals of those selected years on the screen, as well as the name of the scorer and amount of goals scored by it in that year. For this we will use Netbeans and a Model View Controller (MVC).

### Keywords: 
Model View Controller (MVC), OOP Pillars, Graphical environment.

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


## II.	CÓDIGO DE HISTOBET-FEM.

Código comentado para su fácil entendimiento, además de un comentario al inicio de cada clase para mayor comprensión. 

### 1. Se importan las librerías a utilizar. 

import java.util.Scanner;
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

### 2. Se crea el Main que básicamente funciona para llamar la “ventanainiciodesesion”. Que es el método para el acceso del usuario y contraseña. 

public class BetplayLigaFemenina_Grafico {

    public static void main(String[] args) {
        // Crear una ventana de inicio de sesión
        SwingUtilities.invokeLater(() -> {
            VentanaInicioSesion ventanaInicioSesion = new VentanaInicioSesion();
            ventanaInicioSesion.setVisible(true);
        });
    }
}


### 3. Se crea la superclase “Anio”, que llamará los métodos de los demás años y especificará los datos de las finales de cada año. 

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

### 4. Se crea la clase “Anio2020” y otras clases con “Anio2021, 2022 y 2023” en la cual se ingresan los datos de las finales de cada año. Se crean métodos “obtenerInfoAnio” para que pueda ser llamado desde otra clase. Clases Anio, extends Anio.

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



### 5. Se crea la clase Equipo que se encargará de crear el método para obtener el nombre de los equipos. 

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




### 6. Se crea la clase “Final”, que representa los detalles de los partidos de la final en el año que sea solicitado. 

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


### 7. Se crea la clase “Jugadora” que contendrá el método para llamar por el nombre de la jugadora y la cantidad de goles anotados, según el año seleccionado. 

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


### 8.Se crea clase “VentanaInformacionAnio”, la cual se encarga de generar un entorno gráfico en una ventana emergente que muestra la información de el año solicitado. Adicional, se configura su presentación como tamaño de la ventana, titulo de la ventana, botón para “salir” y botón para “regresar”. 

package betplayligafemenina_grafico.Modelo;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class VentanaInformacionAnio extends JFrame {

    public VentanaInformacionAnio(String tituloVentana, String informacionAnio) {
        super(tituloVentana);
        setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
        setSize(600, 400);
        setLocationRelativeTo(null);

        // Crear un panel izquierdo en blanco
        JPanel panelIzquierdo = new JPanel();

        // Establecer el tamaño del panel izquierdo
        panelIzquierdo.setPreferredSize(new Dimension(150, getHeight()));

        // Crear un JPanel para la información con fondo blanco
        JPanel panelInformacion = new JPanel(new BorderLayout());

        // Crear un JTextArea para mostrar la información del año con fondo transparente
        JTextArea textAreaInformacion = new JTextArea(informacionAnio);
        textAreaInformacion.setEditable(false);
        textAreaInformacion.setFont(new Font("Arial", Font.PLAIN, 16));

        // Crear paneles en blanco arriba y debajo del texto
        JPanel panelArriba = new JPanel();
        JPanel panelAbajo = new JPanel();

        // Configurar el diseño de la ventana principal con un BorderLayout
        Container container = getContentPane();
        container.setLayout(new BorderLayout());

        // Agregar el panel izquierdo en el lado izquierdo de la ventana
        container.add(panelIzquierdo, BorderLayout.WEST);

        // Agregar el panel de arriba, el JPanel de información en el centro y el panel de abajo
        container.add(panelArriba, BorderLayout.NORTH);
        container.add(panelInformacion, BorderLayout.CENTER);
        container.add(panelAbajo, BorderLayout.SOUTH);

        // Agregar el JTextArea al panel de información
        panelInformacion.add(textAreaInformacion, BorderLayout.CENTER);

        // Crear un panel para los botones "Volver" y "Salir"
        JPanel panelBotones = new JPanel();
        
        // Crear un botón "Volver" para cerrar esta ventana y volver a la ventana anterior
        JButton botonAtras = new JButton("Volver");
        botonAtras.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                dispose();
            }
        });

        // Crear un botón "Salir" para cerrar toda la aplicación
        JButton botonSalir = new JButton("Salir");
        botonSalir.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                System.exit(0);
            }
        });

        // Agregar los botones "Volver" y "Salir" al panel de botones
        panelBotones.add(botonAtras);
        panelBotones.add(botonSalir);

        // Agregar el panel de botones en la parte inferior
        container.add(panelBotones, BorderLayout.SOUTH);
    }
}

### 9. Se crea la clase “VentanaInicioSesion” que es la que contendrá los JLabel, JTextField, JPasswordField y JButton, para el menú o pantalla de inicio de sesión del usuario, en el cual el usuario será: ciclo3 y la contraseña: proyecto.
Adicional, se crean métodos para la apariencia de la ventana y espacio entre botones. 

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class VentanaInicioSesion extends JFrame {

    // Constructor de la clase
    public VentanaInicioSesion() {
        // Configuración de la ventana principal
        setTitle("***HISTOBET-FEM***"); // Título de la ventana
        setSize(400, 300); // Tamaño de la ventana
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // Cerrar la aplicación al cerrar la ventana
        setLocationRelativeTo(null); // Centrar la ventana en la pantalla
        setResizable(false); // Evitar que la ventana sea redimensionable

        // Creación de un panel para organizar los componentes
        JPanel panel = new JPanel();
        panel.setLayout(new GridBagLayout()); // Utilizar un diseño de cuadrícula para organizar los componentes
        panel.setBackground(new Color(28, 190, 243)); // Establecer el color de fondo del panel

        // Configuración de restricciones para el diseño de cuadrícula
        GridBagConstraints gbc = new GridBagConstraints();
        gbc.insets = new Insets(10, 10, 10, 10); // Espaciado interno entre los componentes

        // Etiqueta que muestra un mensaje informativo
        JLabel labelMensaje = new JLabel("  Inicia sesión para acceder al histórico BetPlay Femenino");
        labelMensaje.setHorizontalAlignment(JLabel.CENTER); // Alinear el texto al centro
        gbc.gridx = 0;
        gbc.gridy = 0;
        gbc.gridwidth = 2;
        panel.add(labelMensaje, gbc);

        // Etiqueta y campo de texto para ingresar el nombre de usuario
        JLabel labelUsuario = new JLabel("Usuario:");
        JTextField campoUsuario = new JTextField();
        campoUsuario.setPreferredSize(new Dimension(250, 30)); // Establecer el tamaño del campo de texto

        // Etiqueta y campo de contraseña
        JLabel labelContrasena = new JLabel("Contraseña:");
        JPasswordField campoContrasena = new JPasswordField();
        campoContrasena.setPreferredSize(new Dimension(250, 30)); // Establecer el tamaño del campo de contraseña

        // Botón para iniciar sesión
        JButton botonIniciarSesion = new JButton("Iniciar Sesión");

        // Botón para mostrar datos de acceso
        JButton botonDatosAcceso = new JButton("Datos de Acceso");
        botonDatosAcceso.setBackground(new Color(28, 147, 250)); // Cambiar el color del botón a verde

        // Botón para salir de la aplicación
        JButton botonSalir = new JButton("Salir");

        // Configuración de las posiciones de los componentes en la cuadrícula
        gbc.gridx = 0;
        gbc.gridy = 1;
        gbc.gridwidth = 1;
        panel.add(labelUsuario, gbc);

        gbc.gridy = 2;
        panel.add(labelContrasena, gbc);

        gbc.gridx = 1;
        gbc.gridy = 1;
        panel.add(campoUsuario, gbc);

        gbc.gridy = 2;
        panel.add(campoContrasena, gbc);

        gbc.gridx = 0;
        gbc.gridy = 3;
        gbc.gridwidth = 2;
        panel.add(botonIniciarSesion, gbc);

        gbc.gridy = 4;
        gbc.insets = new Insets(5, 10, 5, 10); // Espacio entre el botón "Datos de Acceso" y "Salir"
        panel.add(botonDatosAcceso, gbc);

        gbc.anchor = GridBagConstraints.SOUTHEAST; // Alinear el botón "Salir" en la esquina inferior derecha
        gbc.gridy = 5;
        panel.add(botonSalir, gbc);

        // Acción del botón "Iniciar Sesión"
        botonIniciarSesion.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                // Obtener el usuario y la contraseña ingresados
                String usuario = campoUsuario.getText();
                char[] contrasena = campoContrasena.getPassword();
                String contrasenaStr = new String(contrasena);

                // Verificar si el usuario y la contraseña son correctos
                if (usuario.equals("ciclo3") && contrasenaStr.equals("proyecto")) {
                    dispose(); // Cerrar la ventana de inicio de sesión
                    VentanaMenu ventanaMenu = new VentanaMenu(); // Crear una ventana de menú
                    ventanaMenu.setVisible(true); // Mostrar la ventana de menú
                } else {
                    JOptionPane.showMessageDialog(null, "Usuario o contraseña incorrectos", "Error de inicio de sesión", JOptionPane.ERROR_MESSAGE);
                }
            }
        });

        // Acción del botón "Datos de Acceso"
        botonDatosAcceso.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                // Mostrar un mensaje con los datos de acceso
                JOptionPane.showMessageDialog(null, "El usuario es: ciclo3\nLa contraseña es: proyecto", "Datos de Acceso", JOptionPane.INFORMATION_MESSAGE);
            }
        });

        // Acción del botón "Salir"
        botonSalir.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                System.exit(0); // Cerrar la aplicación
            }
        });

        add(panel); // Agregar el panel a la ventana principal
    }

    // Método principal para ejecutar la aplicación
    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new VentanaInicioSesion(); // Crear y mostrar la ventana de inicio de sesión
            }
        });
    }
}

### 10. Se crea la clase: “VentanaMenu”, que será el entorno gráfico donde se encontrará el menú con los años “botones” a seleccionar. Estos botones de cada año estarán asociados al método “mostrarVentanaInformacionAnio” para que, al hacer clic en ellos, se abra la ventana emergente con la información correspondiente a cada año. Se usa el JFrame para la ventana emergente de cada año. Se adiciona el botón de créditos, se ajustan tamaños y se centra el espacio.   

package betplayligafemenina_grafico.Vista;

import betplayligafemenina_grafico.controlador.Anio;
import betplayligafemenina_grafico.controlador.Anio2020;
import betplayligafemenina_grafico.controlador.Anio2021;
import betplayligafemenina_grafico.controlador.Anio2022;
import betplayligafemenina_grafico.controlador.Anio2023;
import betplayligafemenina_grafico.Modelo.VentanaInformacionAnio;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class VentanaMenu extends JFrame {

    public VentanaMenu() {
        // Configuración de la ventana principal
        setTitle("Histórico HISTOBET-FEM"); // Título de la ventana
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // Cerrar la aplicación al cerrar la ventana
        setSize(600, 500); // Tamaño de la ventana
        setLocationRelativeTo(null); // Centrar la ventana en la pantalla
        setResizable(false); // Evitar que la ventana sea redimensionable

        // Establecer el color de fondo de la ventana
        getContentPane().setBackground(new Color(28, 190, 243));

        // Contenedor para el título
        JPanel panelTitulo = new JPanel();
        panelTitulo.setBackground(new Color(28, 190, 243));

        // Contenedor para el mensaje
        JPanel panelMensaje = new JPanel();
        panelMensaje.setBackground(new Color(28, 190, 243));

        // Contenedor para los botones
        JPanel panelBotones = new JPanel(new GridBagLayout());
        panelBotones.setBackground(new Color(28, 190, 243));

        // Crear botones
        JButton[] botones = new JButton[4];
        for (int i = 0; i < 4; i++) {
            botones[i] = crearBoton("Año " + (2020 + i));
            // Establecer el tamaño preferido de los botones
            botones[i].setPreferredSize(new Dimension(200, 40));
        }

        // Botón de créditos
        JButton botonCreditos = crearBoton("Créditos");
        botonCreditos.setBackground(new Color(198, 148, 3)); // Cambiamos el color de fondo del botón Créditos
        // Establecer el tamaño  del botón de créditos
        botonCreditos.setPreferredSize(new Dimension(200, 40));

        // Botón de salir
        JButton botonSalir = crearBoton("Salir");
        botonSalir.setBackground(new Color(192, 192, 192)); // Color gris plata
        botonSalir.setForeground(Color.RED); // Cambiar el color del texto a rojo
        // Establecer el tamaño  del botón de salir
        botonSalir.setPreferredSize(new Dimension(200, 40));

        // Agregar acciones a los botones de año
        for (int i = 0; i < 4; i++) {
            final int anio = 2020 + i;
            botones[i].addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    mostrarInformacionAnio(anio);
                }
            });
        }

        // Agregar acción al botón de créditos
        botonCreditos.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                mostrarCreditos();
            }
        });

        // Agregar acción al botón de salir
        botonSalir.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                System.exit(0);
            }
        });

        // Crear etiquetas de bienvenida y mensaje
        JLabel titulo = new JLabel("Bienvenido a HISTOBET-FEM");
        titulo.setFont(new Font("Arial", Font.BOLD, 18));
        titulo.setHorizontalAlignment(SwingConstants.CENTER);
        titulo.setForeground(Color.BLUE);

        JLabel mensaje = new JLabel("Elija el año del cual desea saber los detalles de la final");
        mensaje.setFont(new Font("Arial", Font.BOLD, 14));
        mensaje.setHorizontalAlignment(SwingConstants.CENTER);
        mensaje.setForeground(Color.BLACK);
        mensaje.setBorder(BorderFactory.createEmptyBorder(10, 0, 20, 0)); // Agrega espacio alrededor del mensaje

        // Configurar las restricciones para centrar los botones
        GridBagConstraints gbc = new GridBagConstraints();
        gbc.gridx = 0;
        gbc.gridy = 0;
        gbc.fill = GridBagConstraints.HORIZONTAL;
        gbc.insets = new Insets(10, 0, 10, 0); // Espacio entre los botones

        // Agregar los botones al panel de botones
        for (int i = 0; i < 4; i++) {
            panelBotones.add(botones[i], gbc);
            gbc.gridy++; // Avanzar a la siguiente fila
        }
        panelBotones.add(botonCreditos, gbc);
        gbc.gridy++;
        panelBotones.add(botonSalir, gbc);

        // Agregar etiquetas y paneles de botones a los contenedores
        panelTitulo.add(titulo);
        panelMensaje.add(mensaje);

        // Agregar los contenedores al contenedor principal
        Container container = getContentPane();
        container.setLayout(new BorderLayout());
        container.add(panelTitulo, BorderLayout.NORTH);
        container.add(panelMensaje, BorderLayout.CENTER);
        container.add(panelBotones, BorderLayout.SOUTH);

        setVisible(true);
    }

    // Método para crear botones con un estilo común
    private JButton crearBoton(String texto) {
        JButton boton = new JButton(texto);
        boton.setFont(new Font("Arial", Font.v, 16)); // Aumentamos el tamaño de la fuente

        // Establecer el fondo del botón
        boton.setBackground(new Color(28, 147, 250));
        boton.setForeground(Color.WHITE); // Cambiamos el color del texto a blanco
        boton.setFocusPainted(false); // Quitamos el efecto de enfoque

        return boton;
    }

    // Método para mostrar información de un año específico
    private void mostrarInformacionAnio(int anio) {
        Anio anioSeleccionado = null;
        switch (anio) {
            case 2020:
                anioSeleccionado = new Anio2020();
                break;
            case 2021:
                anioSeleccionado = new Anio2021();
                break;
            case 2022:
                anioSeleccionado = new Anio2022();
                break;
            case 2023:
                anioSeleccionado = new Anio2023(); 
                break;
        }
        if (anioSeleccionado != null) {
            mostrarVentanaInformacionAnio(anioSeleccionado);
        }
    }

    // Método para mostrar la ventana de información de un año
    private void mostrarVentanaInformacionAnio(Anio anio) {
        VentanaInformacionAnio ventanaInformacionAnio = new VentanaInformacionAnio("Información del Año", anio.obtenerInfoAnio());
        ventanaInformacionAnio.setVisible(true);
    }

    // Método para mostrar los créditos
    private void mostrarCreditos() {
        JOptionPane.showMessageDialog(this, "Créditos:\nCristian De Los Rios\ncristian.de.los.rios@pi.edu.co");
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

