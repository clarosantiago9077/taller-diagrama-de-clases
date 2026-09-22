
SANTIAGO CLARO AGUDELO Y MIGUEL ÁNGEL BLANDÓN ZULUAGA 


# taller-diagrama-de-clases
PARTE 1 - TEORICA
1. Escribe el símbolo UML de cada visibilidad: público, privado, protegido y de paquete :   Público: + ,Privado: - ,Protegido: # ,Paquete: ~
2. ¿Qué relación indica una línea sólida con triángulo hueco? ¿Y una punteada con triángulo hueco?: Línea sólida + triángulo hueco: Herencia / generalización. Línea punteada + triángulo hueco: Realización, normalmente cuando una clase implementa una interfaz.
3.  En un diagrama, ¿cómo distingues una agregación de una composición?: Agregación: rombo hueco ◇. Composición: rombo relleno ◆.
4.  ¿Con qué tipo de línea y qué punta se dibuja una dependencia?: Se dibuja con una línea punteada y una flecha abierta: - - - - >
5.  ¿Cómo se marca una interfaz en el diagrama? ¿Y una clase abstracta?: Interfaz: se representa como una clase con el estereotipo «interface».  Clase abstracta: normalmente se identifica escribiendo el nombre de la clase en cursiva; también puede utilizarse el estereotipo «abstract».
6.  ¿Qué palabras clave de Java limitan qué clases pueden heredar y listan las permitidas?:Se utilizan sealed y permits.
Ejemplo:sealed class Animal permits Perro, Gato
7. ¿Cómo se representa una clase genérica en UML y cómo se llama su vínculo con un tipo concreto?:Una clase genérica se representa con un rectángulo dividido, colocando el parámetro de tipo en un segundo compartimento.
Ejemplo:Caja<T>Cuando se utiliza con un tipo concreto, se establece una relación de sustitución o parametrización del tipo genérico.
8. ¿Qué tipo de relación tiene un record con el tipo de sus componentes?:Un record tiene una relación de composición con sus componentes.
Explicación: Los componentes forman parte del estado del record y están estrechamente ligados a su existencia.
9.Multiplicidad: ¿en qué se traduce en Java un extremo “1” y uno “*”?:1: normalmente se representa con una referencia a un único objeto.
*: normalmente se representa con una colección, como List, Set o Collection.
10.¿Con qué símbolo se indica que una clase está anidada dentro de otra?:Se indica mediante el símbolo de clase anidada, normalmente representado como un rectángulo de clase dentro del rectángulo de la clase exterior.
11.. En JPMS, ¿qué directiva decide qué paquetes son visibles fuera del módulo?:La directiva es exports.
Ejemplo:exports com.ejemplo.modelo;
12.En una interfaz, ¿cuál es la visibilidad por defecto de sus métodos?:Los métodos de una interfaz son public por defecto cuando se declaran como métodos abstractos tradicionales.

PARTE 2 PRACTICA GUIADA
2A. A partir del siguiente código, dibuja su diagrama de clases UML y entrégalo como imagen (PNG). (1,0):

dibujable.java

public interface Dibujable {
    void dibujarse();
}

coordenada.java 

public class Coordenada {
    private int x;
    private int y;

    public Coordenada(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public int getX() {
        return x;
    }

    public void setX(int x) {
        this.x = x;
    }

    public int getY() {
        return y;
    }

    public void setY(int y) {
        this.y = y;
    }
}

punto.java
public class Punto implements Dibujable {
    private Coordenada coordenada;

    public Punto(Coordenada coordenada) {
        this.coordenada = coordenada;
    }

    public Punto(int x, int y) {
        this.coordenada = new Coordenada(x, y);
    }

    public Coordenada getCoordenada() {
        return coordenada;
    }

    public void setCoordenada(Coordenada coordenada) {
        this.coordenada = coordenada;
    }

    @Override
    public void dibujarse() {
        System.out.println("Dibujando punto en las coordenadas (" + coordenada.getX() + ", " + coordenada.getY() + ")");
    }
}

Parte 3 — Modelado autónomo

LIBRO.java

public class Libro {
    String titulo;
    String autor;

    public Libro(String titulo, String autor) {
        this.titulo = titulo;
        this.autor = autor;
    }
}

PRESTAMO.java

public class Prestamo {
    String fecha;
    Libro libro;

    public Prestamo(String fecha, Libro libro) {
        this.fecha = fecha;
        this.libro = libro;
    }
}

SOCIO.java

import java.util.ArrayList;

public class Socio {
    String nombre;
    String numeroCarne;
    ArrayList<Prestamo> prestamos = new ArrayList<>();

    public Socio(String nombre, String numeroCarne) {
        this.nombre = nombre;
        this.numeroCarne = numeroCarne;
    }
}
<img width="652" height="292" alt="diagrama de clases drawio" src="https://github.com/user-attachments/assets/74dbb7fc-cf8f-4c9e-81a3-daf26dc4d01c" />




