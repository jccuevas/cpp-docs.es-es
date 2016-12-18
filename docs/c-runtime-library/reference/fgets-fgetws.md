---
title: "fgets, fgetws | Microsoft Docs"
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
  - "fgets"
  - "fgetws"
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
  - "_fgetts"
  - "fgetws"
  - "fgets"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fgetts (función)"
  - "fgets (función)"
  - "fgetts (función)"
  - "fgetws (función)"
  - "secuencias, obtener cadenas de"
  - "secuencias, leer"
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fgets, fgetws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtenga una cadena de una secuencia.  
  
## Sintaxis  
  
```  
char *fgets(   
   char *str,  
   int n,  
   FILE *stream   
);  
wchar_t *fgetws(   
   wchar_t *str,  
   int n,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `str`  
 Ubicación de almacenamiento de los datos.  
  
 `n`  
 Número máximo de caracteres para leer.  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve `str`.  `NULL` se devuelve para indicar un error o una condición final de archivo.  Utilice `feof` o `ferror` para determinar si se ha producido un error.  Si `str` o `stream` es un puntero NULL, o `n` es menor o igual que cero, esta función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## Comentarios  
 La función de `fgets` lee una cadena de argumento de `stream` de entrada y la almacena en `str`.  `fgets` lee los caracteres de la secuencia actual colocar a e incluir el primer carácter de nueva línea, al final de la secuencia, o hasta la lectura del número de caracteres es igual a `n` – 1, lo que encuentre primero.  El resultado almacenado en `str` se anexa con un carácter nulo.  El carácter de nueva línea, si se lee, se incluye en la cadena.  
  
 `fgetws` es una versión con caracteres anchos de `fgets`.  
  
 `fgetws` lee el argumento `str` de carácter ancho como una cadena de multibyte\- carácter o cadena de caracteres como si `stream` está abierta en modo de texto o modo binario, respectivamente.  Para obtener más información sobre el uso de los modos de texto y binario en E\/S de flujos Unicode y multibyte, vea [E\/S de archivo de modo de texto y binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [E\/S de flujos Unicode en los modos de texto y binario](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_fgetts`|`fgets`|`fgets`|`fgetws`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fgets`|\<stdio.h\>|  
|`fgetws`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fgets.c  
// This program uses fgets to display  
// a line from a file on the screen.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[100];  
  
   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )  
   {  
      if( fgets( line, 100, stream ) == NULL)  
         printf( "fgets error\n" );  
      else  
         printf( "%s", line);  
      fclose( stream );  
   }  
}  
```  
  
## Entrada: crt\_fgets.txt  
  
```  
Line one.  
Line two.  
```  
  
### Resultados  
  
```  
Line one.  
```  
  
## Equivalente en .NET Framework  
  
-   [System::IO::StreamReader::ReadLine](https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline.aspx)  
  
-   [System::IO::TextReader::ReadBlock](https://msdn.microsoft.com/en-us/library/system.io.textreader.readblock.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fputs, fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [gets, \_getws](../../c-runtime-library/gets-getws.md)   
 [puts, \_putws](../../c-runtime-library/reference/puts-putws.md)