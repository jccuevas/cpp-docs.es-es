---
title: "getc, getwc | Microsoft Docs"
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
  - "getwc"
  - "getc"
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
  - "_gettc"
  - "getwc"
  - "_gettchar"
  - "getc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_gettc (función)"
  - "caracteres, leer"
  - "getc (función)"
  - "gettc (función)"
  - "getwc (función)"
  - "getwchar (función)"
  - "leer caracteres de secuencias"
  - "secuencias, leer caracteres de"
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# getc, getwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee un carácter de una secuencia.  
  
## Sintaxis  
  
```  
int getc(   
   FILE *stream   
);  
wint_t getwc(   
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Flujo de entrada.  
  
## Valor devuelto  
 Devuelve el carácter leído.  Para indicar un error de lectura o una condición final de archivo, `getc` vuelve `EOF`, y `getwc` vuelve `WEOF`.  En el caso de `getc`, use `ferror` o `feof` para comprobar si hay un error o una condición de fin de archivo.  Si `stream` es `NULL`, `getc` y `getwc` se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones `EOF` return \(o `WEOF` para`getwc`\) y `errno` determinado a `EINVAL`.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## Comentarios  
 Cada rutina lee un carácter individual de un archivo en la posición actual y aumenta el puntero de archivo asociado \(si se define\) para señalar al carácter siguiente.  El archivo se asocia a `stream`.  
  
 Estas funciones bloquean el subproceso de llamada y son, por consiguiente, seguras para subprocesos.  Para consultar una versión que no realiza el bloqueo, vea [\_getc\_nolock, \_getwc\_nolock](../../c-runtime-library/reference/getc-nolock-getwc-nolock.md).  
  
 Comentarios específicos de la rutina.  
  
|Rutina|Comentarios|  
|------------|-----------------|  
|`getc`|Igual que `fgetc`, pero implementado como función como macro.|  
|`getwc`|Versión de caracteres anchos de `getc`.  Lee un carácter multibyte o un carácter ancho como si `stream` está abierta en modo de texto o modo binario.|  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_gettc`|`getc`|`getc`|`getwc`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`getc`|\<stdio.h\>|  
|`getwc`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_getc.c  
// Use getc to read a line from a file.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
    FILE* fp;  
  
    // Read a single line from the file "crt_getc.txt".   
  
    fopen_s(&fp, "crt_getc.txt", "r");  
    if (!fp)  
    {  
       printf("Failed to open file crt_getc.txt.\n");  
       exit(1);  
    }  
  
    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)  
                         && (ch != '\n'); i++)  
    {  
        buffer[i] = (char) ch;  
    }  
  
    // Terminate string with a null character   
    buffer[i] = '\0';  
    printf( "Input was: %s\n", buffer);  
  
    fclose(fp);  
}  
```  
  
## Entrada: crt\_getc.txt  
  
```  
Line one.  
Line two.  
```  
  
### Resultados  
  
```  
Input was: Line one.  
```  
  
## Equivalente en .NET Framework  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx)  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fgetc, fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [\_getch, \_getwch](../../c-runtime-library/reference/getch-getwch.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc, ungetwc](../../c-runtime-library/reference/ungetc-ungetwc.md)