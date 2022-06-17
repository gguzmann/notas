# CRUD - SPRING BOOT

## INDEX

1.  Estructura proyecto
2.  Dependencias
3.  Configuraciones
4.  Crear modelo
5.  Crear Controlador
6.  Crear Servicio
7.  Crear Repository

## ESTRUCTURA PROYECTO

    src.java
        - api
        - controllers
        - models
        - services
        - repositories
    
    src.main.webapp.WEB-INF
        - Archivos .jsp

    src.resources
        - appplication.properties
                - configuaraciones

    pom.xml

## DEPENDENCIES

en pom.xml agregar las siguientes dependencias:

<details>
<summary>dependencias</summary>
<pre>

    <dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-tomcat</artifactId>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>org.apache.tomcat.embed</groupId>
			<artifactId>tomcat-embed-jasper</artifactId>
		</dependency>
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>jstl</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-validation</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
		</dependency>

		<!-- <dependency> <groupId>org.mindrot</groupId> <artifactId>jbcrypt</artifactId> 
			<version>0.4</version> </dependency> <dependency> <groupId>org.springframework.boot</groupId> 
			<artifactId>spring-boot-starter-security</artifactId> </dependency> -->

	</dependencies>	

</pre>

</details>

## CONFIGURACIONES

En application.properties:

    #Configurar port
	server.port=8080

	#RUTA PARA ACCEDER A JSP
	spring.mvc.view.prefix= /WEB-INF/
	#configuracion base datos
	spring.datasource.url=jdbc:mysql://localhost:3306/generationg1
	spring.datasource.username=israel
	spring.datasource.password=secret

	#CREAR O ACTUALIZAR TABLAS 'create-drop' or 'update'
	spring.jpa.hibernate.ddl-auto=update

	#Nos muestra las querys
	spring.jpa.show-sql= true

## MODELO

> Crear clase Auto en models: en src.java.models:

<details>
<summary>Auto.java</summary>
<pre>

    // PACKAGE
    package com.generation.models;

    // IMPORTACIONES
    import javax.persistence.Entity;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.Table;

    // CREAR TABLA AUTO EN MYSQL
    @Entity
    @Table(name="autos")

    // INICIO CLASE AUTO
    public class Auto {

        //ATRIBUTOS

        // ID PRIMARY KEY AUTO_INCREMENT
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY) //AUTO_INCREMENT
        private Long id;
        
        private String marca;
        private String color;
        private String velocidad;
        private String patente;
        private String precio;
        
        // CONSTRUCTORES
        public Auto() {
            super();
        }


        public Auto(Long id, String marca, String color, String velocidad, String patente, String precio) {
            super();
            this.id = id;
            this.marca = marca;
            this.color = color;
            this.velocidad = velocidad;
            this.patente = patente;
            this.precio = precio;
        }


        // GETTER & SETTERS
        public Long getId() {
            return id;
        }


        public void setId(Long id) {
            this.id = id;
        }


        public String getMarca() {
            return marca;
        }


        public void setMarca(String marca) {
            this.marca = marca;
        }


        public String getColor() {
            return color;
        }


        public void setColor(String color) {
            this.color = color;
        }


        public String getVelocidad() {
            return velocidad;
        }


        public void setVelocidad(String velocidad) {
            this.velocidad = velocidad;
        }


        public String getPatente() {
            return patente;
        }


        public void setPatente(String patente) {
            this.patente = patente;
        }


        public String getPrecio() {
            return precio;
        }


        public void setPrecio(String precio) {
            this.precio = precio;
        }	
    }
</pre>

</details>


## CONTROLADOR

> Crear clase AutoController en services en src.java.controllers:

<details>

<summary>AutoController.java</summary>

<pre>

    // Package
    package com.generation.controllers;

    // Importaciones
    import java.util.List;

    import javax.validation.Valid;

    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.validation.BindingResult;
    import org.springframework.web.bind.annotation.ModelAttribute;
    import org.springframework.web.bind.annotation.PostMapping;
    import org.springframework.web.bind.annotation.RequestMapping;

    import com.generation.models.Auto;
    import com.generation.services.AutoService;

    //Inicializar clase controlador y ruta "/auto"
    @Controller
    @RequestMapping("/auto")
    public class AutoController {

        // Injectar dependecias
        @Autowired
        AutoService autoService;
        
        // GET: Ruta "/auto"
        @RequestMapping("")
        public String indexAuto(Model model ) {
            
            // LLamar metodo getAll de AutoService
            List<Auto> listAuto = autoService.getAll();
            
            // Pasar lista de autos a .jsp
            model.addAttribute("listAuto", listAuto);
                
            return "indexAuto.jsp";
        }
        
        // GET:  Ruta "/register"
        @RequestMapping("/register")

        // Enviar objeto auto vacio
        public String registerAuto(@ModelAttribute("auto") Auto auto) {
            return "registerAuto.jsp";
        }
        
        // POST: Ruta
        @PostMapping("/register/validate")
        // Recibir objeto con datos
        public String validateAuto(@Valid @ModelAttribute("auto") Auto auto,
                BindingResult result,
                Model model) {
            
            // Comprueba si hay errores y devulve mensaje
            if(result.hasErrors()) {
                model.addAttribute("msgError", "Error en ingreso de datos");
                return "registerAuto.jsp";
            }
            
            // Llamar metodo addAuto 
            // Guardar auto en base de datos
            autoService.addAuto(auto);
            
            return "redirect:/auto";
        }
        
        
    }

</pre>

</details>

## .JPS

Agregar archivos .jsp en src.main.webapp.WEB-INF:

<details>

<summary>indexAuto.jsp</summary>

<pre>



    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="ISO-8859-1">
    <title>Insert title here</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-0evHe/X+R7YkIZDRvuzKMRqM+OrBnVFBL6DOitfPri4tjfHxaWutUpFmBp4vmVor" crossorigin="anonymous">
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/js/bootstrap.bundle.min.js" integrity="sha384-pprn3073KE6tl6bjs2QrFaJGz5/SUsLqktiwsUTF55Jfv3qYSDhgCecCxMW52nD2" crossorigin="anonymous"></script>

    </head>
    <body>
    <h1>Bienvenido</h1>
    <h2>Autos:</h2>

    <div class="container">
    <table class="table">
    <thead>
        <tr>
        <th scope="col">#</th>
        <th scope="col">First</th>
        <th scope="col">Last</th>
        <th scope="col">Handle</th>
        </tr>
    </thead>
    <tbody>


    <c:forEach var="autos" items="${listAuto}">

    <tr>
        <th><c:out value="${autos.marca}"></c:out></th>
        <th><c:out value="${autos.color}"></c:out></th>
        <th><c:out value="${autos.precio}"></c:out></th>
        <th> </th>
    </tr>
    </c:forEach>

    </tbody>
    </table>
    </div>
    </body>
    </html>
    
</pre>

</details>


<details>

<summary>registerAuto.jsp</summary>

<pre>


    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
    <%@ taglib prefix="form" uri="http://www.springframework.org/tags/form"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="ISO-8859-1">
    <title>Insert title here</title>
    </head>
    <body>

        <c:out value="${msgError }"></c:out>
        <div>
            <form:form action="/auto/register/validate" method="post" modelAttribute="auto">
                <form:label path="marca">Marca:</form:label>
                <form:input path="marca"/>
                <br>
                <form:label path="color">Color:</form:label>
                <form:input path="color"/>
                <br>
                <form:label path="velocidad">Velocidad Maxima:</form:label>
                <form:input path="velocidad"/>
                <br>
                <form:label path="patente">Patente:</form:label>
                <form:input path="patente"/>
                <br>
                <form:label path="precio">precio:</form:label>
                <form:input path="precio"/>
                <br>
                <input type="submit" value="registrar"/>
            </form:form>
        
        </div>

    </body>
    </html>

</pre>

</details>

## SERVICES

> Crear clase AutoService en services en src.java.services:

<details>

<summary>AutoService.java</summary>

<pre>

    //Package
    package com.generation.services;

    //Import
    import java.util.List;

    import javax.validation.Valid;

    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;

    import com.generation.models.Auto;
    import com.generation.repositories.AutoRepository;

    //Inicio Clase
    @Service
    public class AutoService {

        //Injeccion repository
        @Autowired
        AutoRepository autoRepository;
        
        // Agregar AUTO -> INSERT INTO autos() values();
        public void addAuto(@Valid Auto auto) {
            // TODO Auto-generated method stub
            autoRepository.save(auto);
        }

        // Mostrar AUTOS -> SELECT * FROM autos;
        public List<Auto> getAll() {
            return autoRepository.findAll();
        }

        
    }

</pre>

</details>

## REPOSITORY

> Crear Interfaz AutoRepository en services en src.java.repositories:

<details>

<summary>AutoRepository.java</summary>

<pre>




    // Package
    package com.generation.repositories;

    // Importaciones
    import org.springframework.data.jpa.repository.JpaRepository;
    import org.springframework.stereotype.Repository;

    import com.generation.models.Auto;

    // Inicializar repository y extender a JpaRepository <T,L>
    @Repository
    public interface AutoRepository extends JpaRepository<Auto, Long>{

    }

</pre>

</details>
