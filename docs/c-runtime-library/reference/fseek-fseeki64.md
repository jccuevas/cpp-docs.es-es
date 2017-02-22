---
title: "fseek, _fseeki64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fseeki64"
  - "fseek"
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
apitype: "DLLExport"
f1_keywords: 
  - "fseek"
  - "_fseeki64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fseeki64 (función)"
  - "punteros a archivos [C++]"
  - "punteros a archivos [C++], mover"
  - "fseek (función)"
  - "fseeki64 (función)"
  - "buscar punteros a archivos"
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# fseek, _fseeki64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Mueve el puntero de archivo a una ubicación especificada.  
  
## Sintaxis  
  
```  
int fseek(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
 `offset`  
 Número de bytes de `origin`.  
  
 `origin`  
 Posición inicial.  
  
## Valor devuelto  
 Si es correcto, `fseek` y `_fseeki64` devuelve 0.  De lo contrario, devuelve un valor distinto de cero.  En los dispositivos incapaces de búsqueda, el valor devuelto es indefinido.  Si `stream` es un puntero null, o si `origin` no es uno de valores permitidos descritos a continuación, `fseek` y `_fseeki64` se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven \-1.  
  
## Comentarios  
 `fseek` y `_fseeki64` funciona se desplaza el puntero de archivo \(si existe\) asociado a `stream` a una nueva ubicación que está a bytes de `offset` de *`origin`.* La operación siguiente en la secuencia tiene lugar en la nueva ubicación.  En una secuencia abierto para la actualización, la siguiente operación puede ser una lectura o una escritura.  El origen del argumento debe ser una de las siguientes constantes, definido en STDIO.H:  
  
 `SEEK_CUR`  
 Posición actual del puntero de archivo.  
  
 `SEEK_END`  
 Final de archivo.  
  
 `SEEK_SET`  
 Principio del archivo.  
  
 Puede utilizar `fseek` y `_fseeki64` para colocar el puntero de nuevo en cualquier parte de un archivo.  El puntero se puede colocar más allá del final del archivo.  `fseek` y `_fseeki64`borra la marca de fin de archivo y anula el efecto de cualquier llamada anterior de `ungetc` con `stream`.  
  
 Si se abre para anexar datos, la posición del archivo actual está determinada por la operación de E\/S última, no por donde escribir siguiente aparecería.  Si ninguna operación de E\/S todavía ha producido en un archivo abierto para anexar, la posición del archivo es el inicio del archivo.  
  
 Para las secuencias abierto en el modo de texto, `fseek` y `_fseeki64`limitados uso, porque las traducciones de retorno\- avance de línea de carro pueden producir `fseek` y `_fseeki64`a resultados inesperados de producción.  Únicos `fseek` y operacionesde `_fseeki64`garantizadas para trabajar en secuencias abierto en modo de texto son:  
  
-   Realizar búsquedas con un desplazamiento de 0 en relación con cualquiera de los valores de origen.  
  
-   La búsqueda desde el principio del archivo que devuelva un valor de desplazamiento de una llamada a `ftell` al utilizar `fseek`o `_ftelli64`al utilizar`_fseeki64`.  
  
 También en modo de texto, CTRL\+Z se interpretan como un final de archivo de entrada.  En archivos abierto para lectura\/escritura, `fopen` y toda la comprobación para de rutinas relacionada un CTRL\+Z al final del archivo y quítelo si es posible.  Se hace esto porque utilizar la combinación de `fseek` y `ftell`o`_fseeki64` y `_ftelli64`, para desplazarse en un archivo que finaliza con un CTRL\+Z puede hacer `fseek` o `_fseeki64` para comportarse incorrectamente cerca del final del archivo.  
  
 Cuando abra CRT un archivo que comience con una marca de orden de bytes \(BOM\), el puntero de archivo se coloca después de BOM \(es decir, al inicio del contenido real del archivo\).  Si tiene que `fseek` al principio del archivo, utilice `ftell` de obtener la posición inicial y `fseek` el en lugar de posición 0.  
  
 Esta función bloquea out otros subprocesos durante la ejecución y por consiguiente seguro para subprocesos.  Para consultar una versión que no realiza el bloqueo, vea [\_fseek\_nolock, \_fseeki64\_nolock](../../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md).  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fseek`|\<stdio.h\>|  
|`_fseeki64`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fseek.c  
// This program opens the file FSEEK.OUT and  
// moves the pointer to the file's beginning.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[81];  
   int  result;  
  
   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )  
   {  
      printf( "The file fseek.out was not opened\n" );  
      return -1;  
   }  
   fprintf( stream, "The fseek begins here: "  
                    "This is the file 'fseek.out'.\n" );  
   result = fseek( stream, 23L, SEEK_SET);  
   if( result )  
      perror( "Fseek failed" );  
   else  
   {  
      printf( "File pointer is set to middle of first line.\n" );  
      fgets( line, 80, stream );  
      printf( "%s", line );  
    }  
   fclose( stream );  
}  
```  
  
  **El puntero de archivo se establece en el centro de la primera línea.**  
**Este es el archivo “fseek.out”.**   
## Equivalente en .NET Framework  
  
-   [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
-   [System::IO::FileStream::Seek](https://msdn.microsoft.com/en-us/library/system.io.filestream.seek.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [ftell, \_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [\_lseek, \_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)