# CLASES

> Una clase es un modelo o prototipo de un objeto con atributos, constructor y metodos.
> 
> Objeto: Es la instancia de una clase.
> 
> Instancia de Clase: Se llama instancia a todo objeto que derive de algún otro. De esta forma, todos los objetos son instancias de algún otro.

ESTRUCTURA DE UNA CLASE:
<pre>
public class Cliente {
	// Atributos
	// Constructor
	// Getter & Setter
	// Metodos
}
</pre>

## ATRiBUTOS

**ACCESO** : 
 
	- public: Accesible para todas las clases.
	- private: Accesible solo dentro de la clase actual(this).
	- protected: Accesible a package actual y subclases.
	- default: Accesible desde la clase y el package en que se encuentra.

**TIPO**: primitivo o objeto.

**NOMBRE**: camelCase y que describa su valor.

Ejemplo de atributos:

>		Acceso  -   Tipo    -   Nombre	-	 Valor        
>		private     String      color 	= 	"red";

			// Atributos
			private String nombre;
			private String apellido;
			private int edad;
			private String curso;


### Encapsulamiento de variables:

![Encapsulamiento](/assets/encapsulamiento.png)


## CONSTRUCTOR

Sirve para asignarle valores a nuestro objeto. Por defecto el constructor asignado a una instancia es vacio, no necesita crearlo en el objeto. A menos que cree el constructor con parametros.

Constructor vacio en caso que quiera asignar valor luego de instanciar el objeto.

 Constructor con parametros para instanciar el objeto y asignar valores.

Se pueden crear ambos constructores.

<pre>
//Constructor vacio
	public Alumno() {
		super();
	}

//Constructor con parametros
	public Alumno(String nombre, String apellido, Integer edad, String curso) {
		super();
		this.nombre = nombre;
		this.apellido = apellido;
		this.edad = edad;
		this.curso = curso;
	}
</pre>

## SETTER & GETTER

En caso de que atributos sean privados, para acceder a ellas es necesario crear funciones publicas para modificar o obtener las variables desde afuera. Ocupar this para modificar atributos de clase.

<pre>
// Getter Setter
	public String getNombre() {
		return nombre;
	}

	public void setNombre(String nombre) {
		this.nombre = nombre;
	}
</pre>

## METODOS

Funciones dentro de cada clase.

<pre>
// Metodos
public String toString() {
		return "Alumno [nombre=" + nombre + ", apellido=" + apellido + ", edad=" + edad + ", curso=" + curso + "]";
	}
</pre>

## EJEMPLO CLASE ALUMNO
<pre>
package com.generation.may27; // Package donde se encuentra la clase

public class Alumno {

	// Atributo
	private String nombre;
	private String apellido;
	private int edad;
	private String curso;

	// Constructor
	public Alumno() {
	
	}

	public Alumno(String nombre, String apellido, Integer edad, String curso) {
		super();
		this.nombre = nombre;
		this.apellido = apellido;
		this.edad = edad;
		this.curso = curso;
	}

	// Getter Setter
	public String getNombre() {
		return nombre;
	}

	public void setNombre(String nombre) {
		this.nombre = nombre;
	}

	public String getApellido() {
		return apellido;
	}

	public void setApellido(String apellido) {
		this.apellido = apellido;
	}

	public Integer gerEdad() {
		return edad;
	}

	public void setEdad(Integer edad) {
		this.edad = edad;
	}

	public String getCurso() {
		return curso;
	}

	public void setCurso(String curso) {
		this.curso = curso;
	}

	// Metodos
	public String toString() {
		return "Alumno [nombre=" + nombre + ", apellido=" + apellido + ", edad=" + edad + ", curso=" + curso + "]";
		}

	}

</pre>