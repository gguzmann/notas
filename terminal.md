# Terminal Bash
Indicar ruta donde estoy posicionado '*path*'.

      pw

Lista archivos de rut

      ls
      ls -l: Saber tipo de carpeta y permisos
      ls -a: Mostrar archivos ocultosa

Moverse entre ficheros:

      cd
      cd ..: Volver al fichero anterior.

Limpiar terminal.

      clear

Crear carpeta en ruta.
      
      mkdir '*nameFolder*'

Eliminar archivo.

      rm '*nameFile*'
      rm -f: force.
      rm -r: recursivamente.
      rm -rf: Eliminar carpeta y todo su interior.
        
Crear archivo

      touch '*nameFile*'

Modificar archivo

      nano '*nameFile*'
      -  ctrl + o: Guardar
      -  ctrl + x: Salir

Leer contenido de archivo.

      cat '*nameFile*' 

Copiar archivo.

      cp *'file'* *'to'*
      cp -r: recursividad / Copiar fichero

Buscar palabra en archivo y devuelve la linea donde se encuentra

      grep *'palabra'* *'nameFile'*
      grep -i: mayuscula/minuscula
      grep -r: busca en todo el directorio

## Permisos
    - d : directorio
    - r : read 4
    - w : write 3
    - x : execute 2
  
     ej:
     Permisos
     admin grupoAdmin invitado
     rw-   r--   r-- 
  
