---
title: "Errores potenciales que pasan los objetos de CRT entre los l&#237;mites de DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conflictos de archivos DLL [C++]"
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Errores potenciales que pasan los objetos de CRT entre los l&#237;mites de DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al pasar los objetos de \(CRT\) en tiempo de ejecución de C como identificadores de archivos, configuraciones regionales, y variables de entorno en o DLL \(llamadas a través del límite de DLL\), puede producirse un comportamiento inesperado si el archivo DLL, así como los archivos que llamen al archivo DLL, utilizan diferentes copias de las bibliotecas CRT.  
  
 Un problema relacionado puede aparecer cuando asigna memoria \(explícitamente con `new` o `malloc`, o implícitamente con `strdup`, `strstreambuf::str`, etc.\) y pasa un puntero a través de un límite de DLL que se libere.  Esto puede producir una infracción de acceso de memoria o una daños en la pila si el archivo DLL y sus usuarios utilizan diferentes copias de las bibliotecas CRT.  
  
 Otro síntoma de este problema puede ser un error en la ventana de salida durante la depuración como:  
  
 PILA \[\]: Dirección no válida especificada a RtlValidateHeap \(\#, \#\)  
  
## Causas  
 Cada copia de la biblioteca CRT tiene un estado independiente y distinta.  Como tal, los objetos de CRT como identificadores de archivos, las variables de entorno, y configuraciones regionales sólo son válidos para la copia de CRT donde se asignan o se establecen estos objetos.  Cuando el archivo DLL y sus usuarios utilizan varias copias de la biblioteca CRT, no puede pasar estos objetos CRT a través del límite de DLL y esperar que capture correctamente en el otro lado.  
  
 También, porque cada copia de la biblioteca CRT tiene su propio administrador de pila, asignando memoria en una biblioteca CRT y pasándole el puntero a través de un límite de DLL que se libere por otra copia de la biblioteca CRT es una causa potencial del montón está dañado.  
  
 Si diseña DLL de modo que pasa los objetos de CRT a través del límite o asignar memoria y espera que se liberó fuera de un archivo DLL, se limita a los usuarios DLL para utilizar la misma copia de la biblioteca CRT que DLL.  DLL y sus usuarios utilizan la misma copia de la biblioteca CRT sólo si ambos están vinculados con la misma versión de DLL de CRT.  Esto podría constituir un problema si se mezclan las aplicaciones compiladas con Visual C\+\+ 5,0 con archivos DLL compilados por Visual C\+\+ 4.1 o anterior.  Dado que la versión de DLL de la biblioteca CRT utilizada por Visual C\+\+ 4.1 es msvcrt40.dll y la utilizada por Visual 5,0 es msvcrt.dll, no puede compilar la aplicación para utilizar la misma copia de la biblioteca CRT que estos archivos DLL.  
  
 Sin embargo, hay una excepción.  En la versión en inglés de EE.UU. y otras versiones localizadas de Windows 2000, como el alemán, francés, y Checo, una versión de reenviador de msvcrt40.dll \(versión 4.20\) se envía.  Como resultado, aunque DLL se vincula con msvcrt40.dll y se vinculan al usuario con msvcrt.dll, todavía está utilizando la misma copia de la biblioteca CRT porque todas las llamadas realizadas a msvcrt40.dll se reenvían a msvcrt.dll.  
  
 Sin embargo esta versión de reenviador de msvcrt40.dll no está disponible en algunas versiones localizadas de Windows 2000, como el japonés, coreano, y chino.  Por lo tanto, si la aplicación tiene como destino estos sistemas operativos, necesita cualquiera obtiene una versión actualizada de DLL que no confíe en msvcrt40.dll o modificar la aplicación para que no se basen en utilizar la misma copia de las bibliotecas CRT.  Si ha desarrollado DLL, esto significa recompilarlo con Visual C\+\+ 4,2 o posterior.  Si es un archivo DLL de terceros, debe ponerse en contacto con el proveedor para una actualización.  
  
 Observe que esta versión de DLL de reenviador de msvcrt40.dll \(versión 4.20\) no puede ser redistribuida.  
  
## Ejemplo  
  
### Descripción  
 Este ejemplo pasa un identificador de archivos a través de un límite de DLL.  
  
 El archivo DLL y .exe se compila con \/MD, de modo que comparten una única copia de CRT.  
  
 Si recompila con \/MT para que utilicen copias independientes de CRT, ejecutar el test1Main.exe resultante produce una infracción de acceso.  
  
### Código  
  
```  
// test1Dll.cpp  
// compile with: /MD /LD  
#include <stdio.h>  
__declspec(dllexport) void writeFile(FILE *stream)  
{  
   char   s[] = "this is a string\n";  
   fprintf( stream, "%s", s );  
   fclose( stream );  
}  
```  
  
### Código  
  
```  
// test1Main.cpp  
// compile with: /MD test1dll.lib  
#include <stdio.h>  
#include <process.h>  
void writeFile(FILE *stream);  
  
int main(void)  
{  
   FILE  * stream;  
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );  
   writeFile(stream);  
   system( "type fprintf.out" );  
}  
```  
  
### Resultados  
  
```  
this is a string  
```  
  
## Ejemplo  
  
### Descripción  
 Este ejemplo pasa variables de entorno a través de un límite de DLL.  
  
### Código  
  
```  
// test2Dll.cpp  
// compile with: /MT /LD  
#include <stdio.h>  
#include <stdlib.h>  
  
__declspec(dllexport) void readEnv()  
{  
   char *libvar;  
   size_t libvarsize;  
  
   /* Get the value of the MYLIB environment variable. */   
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );  
  
   if( libvar != NULL )  
      printf( "New MYLIB variable is: %s\n", libvar);  
   else  
      printf( "MYLIB has not been set.\n");  
   free( libvar );  
}  
```  
  
### Código  
  
```  
// test2Main.cpp  
// compile with: /MT /link test2dll.lib  
#include <stdlib.h>  
#include <stdio.h>  
  
void readEnv();  
  
int main( void )  
{  
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );  
   readEnv();  
}  
```  
  
### Resultados  
  
```  
MYLIB has not been set.  
```  
  
 Si el archivo DLL y el archivo .exe se compilan con \/MD para utilizar sólo una copia de CRT, el programa se ejecuta correctamente y genera el siguiente resultado:  
  
```  
New MYLIB variable is: c:\mylib;c:\yourlib  
```  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)