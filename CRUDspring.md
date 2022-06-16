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

</details>

## SERVICES

> Crear clase AutoService en services en src.java.services:

<details>
<summary>AutoService.java</summary>

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


</details>

## REPOSITORY

> Crear Interfaz AutoRepository en services en src.java.repositories:

<details>
<summary>AutoRepository.java</summary>

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


</details>

## CONTROLADOR

> Crear clase AutoController en services en src.java.controllers:

<details>
<summary>AutoController.java</summary>

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


</details>

