---
title: "vfscanf, vfwscanf | Microsoft Docs"
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
  - "vfwscanf"
  - "vfscanf"
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
  - "vfwscanf"
  - "_vftscanf"
  - "vfscanf"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: c06450ef-03f1-4d24-a8ac-d2dd98847918
caps.latest.revision: 6
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vfscanf, vfwscanf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee datos con formato de un flujo.  Hay disponibles versiones más seguras de estas funciones; vea [vfscanf\_s, vfwscanf\_s](../../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md).  
  
## Sintaxis  
  
```  
int vfscanf(   
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int vfwscanf(   
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
 `format`  
 Cadena de control de formato.  
  
 `arglist`  
 Lista de argumentos de variable.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el número de campos que se convierten y asignan correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron.  Un valor devuelto de 0 indica que no se ha asignado ningún campo.  Si se produce un error, o si se llega al final del flujo de archivo antes de la primera conversión, el valor devuelto es `EOF` para `vfscanf` y `vfwscanf`.  
  
 Estas funciones validan sus parámetros.  Si `stream` o `format` es un puntero NULL, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
## Comentarios  
 La función `vfscanf` lee datos de la posición actual de `stream` en las ubicaciones que se proporcionan por la lista de argumentos `arglist`.  Cada argumento de la lista debe ser un puntero a una variable de un tipo que se corresponda con un especificador de tipo en `format`.  `format` controla la interpretación de los campos de entrada y tiene el mismo formulario y función que el argumento `format` para `scanf`; vea [scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) para obtener una descripción de `format`.  
  
 `vfwscanf` es una versión con caracteres anchos de `vfscanf`; el argumento de formato para `vfwscanf` es una cadena de caracteres anchos.  Estas funciones se comportan exactamente igual si la secuencia se abre en modo ANSI.  `vfscanf` no admite la entrada desde una secuencia de UNICODE.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vftscanf`|`vfscanf`|`vfscanf`|`vfwscanf`|  
  
 Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`vfscanf`|\<stdio.h\>|  
|`vfwscanf`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_vfscanf.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses vfscanf to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdarg.h>  
  
FILE *stream;  
  
int call_vfscanf(FILE * istream, char * format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vfscanf(istream, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main(void)  
{  
    long l;  
    float fp;  
    char s[81];  
    char c;  
  
    if (fopen_s(&stream, "vfscanf.out", "w+") != 0)  
    {  
        printf("The file vfscanf.out was not opened\n");  
    }  
    else  
    {  
        fprintf(stream, "%s %ld %f%c", "a-string",  
            65000, 3.14159, 'x');  
        // Security caution!  
        // Beware loading data from a file without confirming its size,  
        // as it may lead to a buffer overrun situation.  
  
        // Set pointer to beginning of file:  
        fseek(stream, 0L, SEEK_SET);  
  
        // Read data back from file:  
        call_vfscanf(stream, "%s %ld %f%c", s, &l, &fp, &c);  
  
        // Output data read:   
        printf("%s\n", s);  
        printf("%ld\n", l);  
        printf("%f\n", fp);  
        printf("%c\n", c);  
  
        fclose(stream);  
    }  
}  
  
```  
  
  **a\-string**  
**65000**  
**3.141590**  
**x**   
## Equivalente en .NET Framework  
 [System::IO::StreamReader::ReadLine](https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline.aspx). Vea también los métodos `Parse`, como [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_cscanf, \_cscanf\_l, \_cwscanf, \_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [fscanf\_s, \_fscanf\_s\_l, fwscanf\_s, \_fwscanf\_s\_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)   
 [vfscanf\_s, vfwscanf\_s](../../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md)