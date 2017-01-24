---
title: "fgetpos | Microsoft Docs"
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
  - "fgetpos"
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
  - "fgetpos"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fgetpos (función)"
  - "secuencias, indicador de posición de archivo"
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fgetpos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene el marcador del archivo \(el archivo posición de una secuencia.  
  
## Sintaxis  
  
```  
int fgetpos(   
   FILE *stream,  
   fpos_t *pos   
);  
```  
  
#### Parámetros  
 `stream`  
 Secuencia de destino.  
  
 `pos`  
 Almacenamiento de Posición\- indicador.  
  
## Valor devuelto  
 Si es correcto, `fgetpos` devuelve 0.  En el error, devuelve un valor distinto de cero y establece `errno` a una de las constantes de manifiesto siguientes \(definidas en STDIO.H\): `EBADF`, lo que significa que la secuencia especificada no es un puntero de archivo válido o no es accesible, o `EINVAL`, que significa que el valor de `stream` o el valor de `pos` es válida, por ejemplo si alguno es puntero NULL.  Si `stream` o `pos` es un puntero de `NULL` , la función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## Comentarios  
 La función de `fgetpos` obtiene el valor actual del indicador del archivo \(el archivo posición del argumento de `stream` y lo almacena en el objeto indicada por `pos`.  La función de `fsetpos` puede utilizar después la información almacenada en `pos` para restaurar el puntero de argumento de `stream` a su posición cuando `fgetpos` se llamó.  El valor de `pos` se almacena en un formato interno y se ha diseñado para su uso con por `fgetpos` y `fsetpos`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fgetpos`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fgetpos.c  
// This program uses fgetpos and fsetpos to  
// return to a location in a file.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE   *stream;  
   fpos_t pos;  
   char   buffer[20];  
  
   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {  
      perror( "Trouble opening file" );  
      return -1;  
   }  
  
   // Read some data and then save the position.   
   fread( buffer, sizeof( char ), 8, stream );  
   if( fgetpos( stream, &pos ) != 0 ) {  
      perror( "fgetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fgetpos: %.13s\n", buffer );  
  
   // Restore to old position and read data   
   if( fsetpos( stream, &pos ) != 0 ) {  
      perror( "fsetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fsetpos: %.13s\n", buffer );  
   fclose( stream );  
}  
```  
  
## Entrada: crt\_fgetpos.txt  
  
```  
fgetpos gets a stream's file-position indicator.  
```  
  
### Salida crt\_fgetpos.txt  
  
```  
after fgetpos: gets a stream  
after fsetpos: gets a stream  
```  
  
## Equivalente en .NET Framework  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fsetpos](../../c-runtime-library/reference/fsetpos.md)