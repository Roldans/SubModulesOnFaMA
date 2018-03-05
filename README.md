 # SubModulesOnFaMA

Actualmente el repositorio [FaMA] tiene varios proyectos en su interior, desde los sistemas de modelos,  a los razonadores, todo en un solo proyecto git, visto el estado actual de FaMA, propongo el uso de [submodulos] de git de manera que cada proyecto ternga su propio repositorio y los cambios en estos estén reflejados en su propio git.

De esta manera se podria trabajar en un proyecto de forma aislada y se podría hacer un mejor seguimiento de su evolución ademas de realizar pruebas y comprobar el buen funcionamiento de cada modulo de manera independiente si tener que realizar pruebas al sistema completo.


![Image of submodules](https://raw.githubusercontent.com/Roldans/SubModulesOnFaMA/master/submodules.jpg)


## Usando submodulos:
* Clonar un repo:
   
   `$ git clone git://github.com/XXXX/myproject.git`
 
    `$ cd myproject`
 
    `$ git submodule init`
 
    `$ git submodule update`
* Añadir submodulos:
 
   `$ git submodule add http:\\porject-url`

* Borrar submodilos:
  
   Desinicializamos el submódulo de la lista de submódulos
  
    `$ git submodule deinit path/submodule`
  
   Borramos físicamente el directorio del submódulo
  
    `$ git rm path/submodule`
  
   Eliminar cache del árbol de trabajo de Git
  
    `$ git rm --cached path/submodule`
  
  Eliminamos la meta información del submódulo que por alguna razón no borra Git
  
   `$ rm -rf .git/modules/path/submodule`
   
 * Posibles problemas al usar submodulos:
  
   * Cambios en un submodulo con cabecera desconectada:
  Este problema ocurre cuando trabajamos en la carpeta de un submodulo y lanzar el comando `git submudole update` desde la carpeta del proyecto padre sin haber hecho commit de los cambios, git "sobreescribirá" la carpeta del submodulo sin avisar. Realmente no se pierden los datos como tal solo que no hay ningun puntero sobre esos cambios. Para evistar esto cuando se vaya a trabajar sobre la carpeta de un submodulo de manera que aunque se sobreescriba la carpeta del submodulo tendremos un puntero al trabajo realizado en dicha rama.
   
   * Usar ramas con submódulos tiene también sus peculiaridades. Si se crea una rama, se añade un submódulo en ella y luego se fusiona a una rama donde dicho submódulo no exista. La carpeta del submódulo sigue existiendo, solo que ahora queda como una carpeta sin seguimiento. Por lo que perderiamos datos locales si no fueron enviados al servidor primero.
   
   * A la hora de cambiar carpetas por submodulos, hay que tener cuidado, si borramos la carpeta y intentamos añadir un modulo, git nos dirá que dicha carpeta ya existe. Deberiamos sacar la carpeta inicial del entorno de trabajo con `git rm -r carpeta`
  
  [FaMA]: <https://github.com/isa-group/FaMA>
  [submodulos]: <https://git-scm.com/book/es/v1/Las-herramientas-de-Git-Subm%C3%B3dulos>
