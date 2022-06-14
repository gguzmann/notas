# SPRING BOOT

## MVC

Vista: html - css -jsp - js -> react - angular - vuejs
controlador: clases java-> controllers - services - repositories
modelo: clases java-> objetos - entidades


## RUTAS 
@RequestMapping("/nombreRuta") // antes de cada clase. No va con ; al final
@RequestMapping(value = "/clients/register", method= RequestMethod.GET) // Otra forma de enrutamiento

public String users() {
		return "usuarios"; // Lo que devuelve al ingresar a localhost:8080/nombreRuta
	}


//INDICAR RUTA
//PATH: localhost:8080/index

@RequestMapping("/nombreRuta") // antes de cada clase. No va con ; al final
@RequestMapping(value = "/clients/register", method= RequestMethod.GET) // Otra forma de enrutamiento




## ENVIAR DATOS
//INDICAR ENVIAR DATOS SOLO POR POST
@RequestPost("/")

//INDICAR PARAMETRO
//PATH: localhost:8080/index?pagina=9 -> parametro pagina = 9
@RequestParam(value="nameParam") String nameVar // Por defecto requiere el parametro en la url, si no da error
@RequestParam(value="nameParam", required = false) String nameVar // si no viene en url marca null

//INDICAR VARIABLE EN RUTA(PATH)
//PATH: localhost:8080/users/juan -> variable = juan
@PathVariable("nameVar) String nameVar



## FORMULARIO CONTROLLER

	//PAGINA REGISTRO CON MODELO
	@RequestMapping("")
	public String register(@ModelAttribute("usuario") Usuario usuario) { // Pasar obj vacio
		return "register.jsp";
	}

	//CAPTURAR DATOS AL MODELO USUARIO
	@PostMapping("/user")
	public String registerUser(@ModelAttribute("usuario") Usuario usuario) {
		System.out.println(usuario.getNombre()+" "+usuario.getApellido()+" edad: "+usuario.getEdad());
		return "register.jsp";
	}

## ESTRUCTURA BASICA JSP

	<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
	<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>				-- ENVIAR DATOS DESDE CONTROLADOR A VIEW
	<%@ taglib prefix="form" uri="http://www.springframework.org/tags/form"%>	-- FORMULARIOS
	<!DOCTYPE html>
	<html>
	<head>
	<meta charset="UTF-8">
	<title>Insert title here</title>
	</head>
	<body>

		//FORMULARIO INDICANDO MODELATTRIBUTE usuario
		<form:form action="/register/user" autocomplete="off" method="post" modelAttribute="usuario">
			<form:label path="nombre">Nombre:</form:label>
			<form:input path="nombre"/>
			<br>
			<form:label path="apellido">Apellido:</form:label>
			<form:input path="apellido"/>
			<br>
			<form:label path="edad">Edad:</form:label>
			<form:input type="number" path="edad"/>
			<br>
			<input type="submit" value="Enviar"/>
		</form:form>

	</body>
	</html>
