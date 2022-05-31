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

ACCESO : 
 
	- public: Accesible para todas las clases.
	- private: Accesible solo dentro de la clase actual(this).
	- protected:  
	- default: Accesible desde la clase y el package en que se encuentra.

TIPO: primitivo o objeto.

NOMBRE: camelCase y que describa su valor.


    //  Acceso  -   Tipo    -   Nombre - Valor
        private     String      color = "red";

### Encapsulamiento de variables:

![Encapsulamiento](/assets/encapsulamiento.png)


## CONSTRUCTOR

Por defecto el constructor asignado a una instancia es vacio, no necesita crearlo en el objeto. A menos que cree el constructor con parametros.

<pre>
	public Alumno(String nombre, String apellido, Integer edad, String curso) {
		super();
		this.nombre = nombre;
		this.apellido = apellido;
		this.edad = edad;
		this.curso = curso;
	}
</pre>

## SETTER & GETTER

## METODOS

## EJEMPLO CLASE ALUMNO
<pre>
package com.generation.may27;

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

}

</pre>