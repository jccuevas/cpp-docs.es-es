---
title: "fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l | Microsoft Docs"
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
  - "fwscanf_s"
  - "_fscanf_s_l"
  - "_fwscanf_s_l"
  - "fscanf_s"
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
  - "_fwscanf_s_l"
  - "_fscanf_s_l"
  - "fscanf_s"
  - "_ftscanf_s_l"
  - "_ftscanf_s"
  - "fwscanf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fscanf_s_l (función)"
  - "_ftscanf_s (función)"
  - "_ftscanf_s_l (función)"
  - "_fwscanf_s_l (función)"
  - "datos [CRT], leer secuencias"
  - "datos con formato [C++], leer secuencias"
  - "fscanf_s (función)"
  - "fscanf_s_l (función)"
  - "ftscanf_s (función)"
  - "ftscanf_s_l (función)"
  - "fwscanf_s (función)"
  - "fwscanf_s_l (función)"
  - "secuencias [C++], leer datos con formato de"
ms.assetid: b6e88194-714b-4322-be82-1cc0b343fe01
caps.latest.revision: 28
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee datos con formato de un flujo.  Estas versiones de [fscanf, \_fscanf\_l, fwscanf, \_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
int fscanf_s(   
   FILE *stream,  
   const char *format [,  
   argument ]...   
);  
int _fscanf_s_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...   
);  
int fwscanf_s(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...   
);  
int _fwscanf_s_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]...   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
 `format`  
 Cadena de control de formato.  
  
 `argument`  
 Argumentos opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el número de campos que se convierten y asignan correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron.  Un valor devuelto de 0 indica que no se ha asignado ningún campo.  Si se produce un error, o si se llega al final del flujo de archivo antes de la primera conversión, el valor devuelto es `EOF` para `fscanf_s` y `fwscanf_s`.  
  
 Estas funciones validan sus parámetros.  Si `stream` es un puntero de archivo no válido o `format` es un puntero nulo, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
## Comentarios  
 La función `fscanf_s` lee datos de la posición actual de `stream` en las ubicaciones que proporciona`argument` \(de haberlas\).  Cada `argument` debe ser un puntero a una variable de un tipo que se corresponda con un especificador de tipo en `format`.  `format` controla la interpretación de los campos de entrada y tiene el mismo formato y función que el argumento de `format` para `scanf_s`. Vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) para obtener una descripción de `format`. `fwscanf_s` es una versión con caracteres anchos de `fscanf_s`; el argumento de formato para `fwscanf_s` es una cadena de caracteres anchos.  Estas funciones se comportan igual si el flujo se abre en modo ANSI.  `fscanf_s` no admite actualmente la entrada desde un flujo UNICODE.  
  
 La diferencia principal entre las funciones más seguras \(que tienen el sufijo `_s`\) y las demás versiones es que las funciones más seguras requieren el tamaño en caracteres de cada `c`, `C`, `s`, `S` y el campo de tipo `[` que se va a pasar como argumento inmediatamente después de la variable.  Para obtener más información, vea [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) y [scanf \(Especificación de ancho\)](../../c-runtime-library/scanf-width-specification.md).  
  
> [!NOTE]
>  El parámetro de tamaño es del tipo `unsigned`, no `size_t`.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ftscanf_s`|`fscanf_s`|`fscanf_s`|`fwscanf_s`|  
|`_ftscanf_s_l`|`_fscanf_s_l`|`_fscanf_s_l`|`_fwscanf_s_l`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fscanf_s`, `_fscanf_s_l`|\<stdio.h\>|  
|`fwscanf_s`, `_fwscanf_s_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_fscanf_s.c  
// This program writes formatted  
// data to a file. It then uses fscanf to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long l;  
   float fp;  
   char s[81];  
   char c;  
  
   errno_t err = fopen_s( &stream, "fscanf.out", "w+" );  
   if( err )  
      printf_s( "The file fscanf.out was not opened\n" );  
   else  
   {  
      fprintf_s( stream, "%s %ld %f%c", "a-string",   
               65000, 3.14159, 'x' );  
      // Set pointer to beginning of file:  
      fseek( stream, 0L, SEEK_SET );  
  
      // Read data back from file:  
      fscanf_s( stream, "%s", s, _countof(s) );  
      fscanf_s( stream, "%ld", &l );  
  
      fscanf_s( stream, "%f", &fp );  
      fscanf_s( stream, "%c", &c, 1 );  
  
      // Output data read:  
      printf( "%s\n", s );  
      printf( "%ld\n", l );  
      printf( "%f\n", fp );  
      printf( "%c\n", c );  
  
      fclose( stream );  
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
 [\_cscanf\_s, \_cscanf\_s\_l, \_cwscanf\_s, \_cwscanf\_s\_l](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)   
 [fprintf\_s, \_fprintf\_s\_l, fwprintf\_s, \_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf\_s, \_sscanf\_s\_l, swscanf\_s, \_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [fscanf, \_fscanf\_l, fwscanf, \_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)