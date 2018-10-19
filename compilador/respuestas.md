1. Que se espera de cada uno de estos pasos: 

* Pre-procesador: `make preprocessing`
Se espera que se genere un archivo de texto con un preproceso del archivo fuente, 
es decir agregando ciertos macros e includes que se indican. En este caso #include "calculator.h"

* Compilacion I: `make assembler`
Se espera que se genere un archivo de texto con lenguaje assembler a partir del archivo generado
en el paso anterior.

* Compilacion II: `make object`
Se espera que se genere un archivo binario con el modelo de objetos, código maquina que aun
no puede ejecutarse porque falta hacer el linkeo.

* Linkeo: `make executable`
Se espera que se genere un archivo ejecutable con codigo maquina.

2. ¿Qué agregó el preprocesador?

* Agregó el stdio.h debido al llamado a la funcion printf.

3. Identificar en la rutina de assembler las funciones

* linea 22 -> call	_add_numbers
* linea 27 -> call	_printf

4. Explicar qué quieren decir los símbolos que se crean en el objeto

* 0000000000000050 T _add_numbers     ->      Es una funcion exportable
* 0000000000000000 T _main            ->      Es otra funcion exportable
*                  U _printf          ->      Es una funcion indefinida

5. ¿En qué se diferencian los símbolos del objeto y del ejecutable?

* 0000000100000000 T __mh_execute_header
* 0000000100000f60 T _add_numbers
* 0000000100000f10 T _main
*                  U _printf
*                  U dyld_stub_binder

Se diferencian en que en el ejecutable se agrega (U dyld_stub_binder) una función indefinida
que supongo se encarga de manejar las librerias dinamicas.
Tambien se agrega (0000000100000000 T __mh_execute_header) que es una funcion exportable que 
supongo se encarga de ejecutar el header.
Además cambian las direcciones  de memoria.