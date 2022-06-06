Preprocesador:

Comenzamos con la creacion de hello2.c que contiene el siguiente codigo:

    #include <stdio.h>
    int/*medio*/main(void){
    int i=42;
    prontf("La respuesta es %d\n");

Para generar hello2.i se debe ejecutar la siguiente linea de código:

 gcc hello2.c -E -o hello2.i
 
 como resultado obteneremos el contenido de hello2.c mas el agregado de stdio.h(ademas quita los comentarios en hello2.c)
 
 Diferencias entre hello2.c y hello2.i 
 
 solo se agregaron un par de lineas por encima del codigo de hello2.c que se refieren a las funcionalidades que utiliza hello2.c
 
 Siguiente paso escribir hello3.c que contendra el siguiente codigo:

    int printf(const char * restrict s, ...);
    int main(void){
    int i=42;
    prontf("La respuesta es %d\n");
   
   En la primera linea se declara la funcion de printf con un puntero a char como argumento , el cual solo el puntero es costante .
   
   hello3.i contiene el siguiente codigo:
   
    # 1 "hello3.c"
    # 1 "<built-in>"
    # 1 "<command-line>"
    # 1 "hello3.c"
    int printf(const char * restrict s, ...);
    int main(void){
    int i=42;
    prontf("La respuesta es %d\n");

El cual a diferencia de hello3.c se le agregaron 4 lineas por encima de la declaracion de printf.Estas mismas lineas aparecieron en el principio de hello2.i pero a diferencia de hello3 ,hello2 contenia a studio.h que nos da un encabezado con mas fucncionalidades que hello3.i .

Compilacion:

Para realizar la compilacion y no ensamblacion de hello3.c se utilizo el siguiente comando que genero el hello3.o:

    gcc hello3.c -S -o hello3.s

![image](https://user-images.githubusercontent.com/44420382/172086874-3c739a0c-6559-43f2-b963-033f922a3446.png)

como observamos la funcion prontf no fue declarada y nos ofrece una posible opcion para resolverlo con printf, ademas tenemos una falta de } en la funcion main.Corregimos el codigo y volvemos a probar.

    int printf(const char * restrict s, ...);
    int main(void){
    int i=42;
    prontf("La respuesta es %d\n");
    }
    
![image](https://user-images.githubusercontent.com/44420382/172087339-66035f63-46fc-4fb0-b2d1-a4e261c44c8d.png)

Obtenemos el archivo hello4.s que es un archivo que contiene el codigo assembler correspondiente al hello4.c.Pareceria una locura pensar que ese codigo realiza las mismas tareas que hello4.c especifica pero en realidad es la finalidad de los .s ,la cual es contener el codigo assembler correspondiente al codigo de hello4.c,en este paso pasamos de un lenguje de alto nivel como lo es c a un lenguaje de bajo nivel como es assembler

Con el siguiente comando pasamos del hello4.s a hello4.o, con el cual creamos el archivo objeto 

    gcc hello4.s -c -o hello4.o
    
Vinculacion:

