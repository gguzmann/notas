# CLASES

> Una clase es un modelo o prototipo de un objeto con atributos, constructor y metodos.
> 
> Objeto: Es la instancia de una clase.
> 
> Instancia de Clase: Se llama instancia a todo objeto que derive de algún otro. De esta forma, todos los objetos son instancias de algún otro.

## ATRiBUTOS

>ACCESO : public - private - protected -> Encapsulamiento de variables.
>
>TIPO: primitivo o objeto.
>
>NOMBRE: camelCase.


    //  Acceso  -   Tipo    -   Nombre - Valor
        private -   String  -   color = "red";

## CONSTRUCTOR

## METODOS


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