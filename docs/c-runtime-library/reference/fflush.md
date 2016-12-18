---
title: "fflush | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fflush"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fflush"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fflush (función)"
  - "vaciar"
  - "secuencias, vaciar"
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
caps.latest.revision: 18
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fflush
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Vacía una secuencia.  
  
## Sintaxis  
  
```  
int fflush(   
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 `fflush` devuelve 0 si el búfer se vaciado correctamente.  El valor 0 también se devuelve en casos en los que la secuencia especificada no tiene ningún búfer o está abierto para lectura únicamente.  Un valor devuelto de `EOF` indica un error.  
  
> [!NOTE]
>  Si `fflush` devuelve `EOF`, los datos podrían haber perdido debido a un error de escritura.  Al configurar un controlador de error crítico, resulta más seguro activar el almacenamiento en búfer desactivado con la función de `setvbuf` o utilizar las rutinas de E\/S de bajo nivel como `_open`, `_close`, y `_write` en lugar de E\/S de secuencia funciona.  
  
## Comentarios  
 La función de `fflush` vacía una secuencia.  Si el archivo asociado a `stream` está abierto para la salida, `fflush` escribe en ese archivo el contenido del búfer asociado a la secuencia.  Si la secuencia está abierto para la entrada, `fflush` borra el contenido del búfer.  `fflush` anula el efecto de cualquier llamada anterior a `ungetc` con `stream`.  Además, `fflush(NULL)` vacía todas las secuencias abierto para la salida.  La secuencia permanece abierto después de la llamada.  `fflush` no tiene ningún efecto en una secuencia inseparada.  
  
 Los búferes son mantenidas normalmente por el sistema operativo, que determina el tiempo óptima de escribir los datos automáticamente en disco: cuando el búfer está lleno, cuando se cierra una secuencia, o cuando un programa finaliza normalmente sin cerrar la secuencia.  La característica de confirmación\-a\- disco de la biblioteca en tiempo de ejecución permite asegurarse que los datos crítico se escribe directamente en el disco y no a los búferes del sistema operativo.  Sin volver a escribir un programa existente, puede habilitar esta característica vincular los archivos objeto program con COMMODE.OBJ.  En el archivo ejecutable resultante, las llamadas a `_flushall` escriben el contenido de todos los búferes en el disco.  Sólo `_flushall` y `fflush` afectados por COMMODE.OBJ.  
  
 Para obtener información sobre cómo controlar la característica de confirmación en disco, vea [E\/S de flujos](../../c-runtime-library/stream-i-o.md), [fopen](../../c-runtime-library/reference/fopen-wfopen.md) y [\_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md).  
  
 Esta función bloquea el subproceso de la llamada y por consiguiente seguro para subprocesos.  Para consultar una versión que no realiza el bloqueo, vea `_fflush_nolock`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fflush`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fflush.c  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int integer;  
   char string[81];  
  
   // Read each word as a string.  
   printf( "Enter a sentence of four words with scanf: " );  
   for( integer = 0; integer < 4; integer++ )  
   {  
      scanf_s( "%s", string, sizeof(string) );        
      printf( "%s\n", string );  
   }  
  
   // You must flush the input buffer before using gets.   
   // fflush on input stream is an extension to the C standard   
   fflush( stdin );     
   printf( "Enter the same sentence with gets: " );  
   gets_s( string, sizeof(string) );  
   printf( "%s\n", string );  
}  
```  
  
  **`Esto es una prueba Este es el testThis`  `es una prueba Esto es un testEnter`a la frase de cuatro palabras con scanf: Esto es una prueba**  
**Este objeto .**  
**es**  
**a**  
**prueba**  
**Escriba la misma frase con obtiene: Esto es una prueba**  
**Esto es una prueba**   
## Equivalente en .NET Framework  
 [System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fclose, \_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)