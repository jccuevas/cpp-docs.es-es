---
title: fscanf, _fscanf_l, fwscanf, _fwscanf_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fscanf
- _fwscanf_l
- _fscanf_l
- fwscanf
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- fscanf
- fwscanf
- _ftscanf_l
- _fwscanf_l
- _ftscanf
- _fscanf_l
dev_langs:
- C++
helpviewer_keywords:
- fscanf function
- fwscanf function
- formatted data [C++], reading from streams
- ftscanf_l function
- _ftscanf_l function
- _fwscanf_l function
- data [CRT], reading from streams
- _fscanf_l function
- ftscanf function
- fscanf_l function
- streams [C++], reading formatted data from
- _ftscanf function
- fwscanf_l function
ms.assetid: 9004e978-6c5f-4bb2-98fd-51e5948933f2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa3ccb3cc8a528847b39ad16d5e90d17e24b1da0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="fscanf-fscanfl-fwscanf-fwscanfl"></a>fscanf, _fscanf_l, fwscanf, _fwscanf_l
Lea datos con formato en una secuencia. Hay disponibles versiones más seguras de estas funciones; consulte [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int fscanf(   
   FILE *stream,  
   const char *format [,  
   argument ]...   
);  
int _fscanf_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...   
);  
int fwscanf(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...   
);  
int _fwscanf_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]...   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura `FILE` .  
  
 `format`  
 Cadena de control de formato.  
  
 `argument`  
 Argumentos opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve el número de campos convertidos y asignados correctamente; el valor devuelto no incluye los campos que se han leído pero no se han asignado. Un valor devuelto de 0 indica que no se ha asignado ningún campo. Si se produce un error, o si se llega al final del flujo de archivo antes de la primera conversión, el valor devuelto es `EOF` para `fscanf` y `fwscanf`.  
  
 Estas funciones validan sus parámetros. Si `stream` o `format` es un puntero nulo, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `fscanf` lee datos desde la posición actual de `stream` en las ubicaciones que `argument` proporciona (de haberlas). Cada `argument` debe ser un puntero a una variable de un tipo que se corresponda con un especificador de tipo en `format`. `format` controla la interpretación de los campos de entrada y tiene el mismo formato y función que el argumento `format` de `scanf`. Vea [scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) para obtener una descripción de `format`.  
  
 `fwscanf` es una versión con caracteres anchos de `fscanf`; el argumento de formato para `fwscanf` es una cadena de caracteres anchos. Estas funciones se comportan de forma idéntica si la secuencia se abre en modo ANSI. `fscanf` no admite actualmente la entrada desde un flujo UNICODE.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ftscanf`|`fscanf`|`fscanf`|`fwscanf`|  
|`_ftscanf_l`|`_fscanf_l`|`_fscanf_l`|`_fwscanf_l`|  
  
 Para obtener más información, consulte [campos de especificación de formato: funciones scanf y Wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`fscanf`, `_fscanf_l`|\<stdio.h>|  
|`fwscanf`, `_fwscanf_l`|\<stdio.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_fscanf.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses fscanf to  
// read the various data back from the file.  
  
#include <stdio.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long l;  
   float fp;  
   char s[81];  
   char c;  
  
   if( fopen_s( &stream, "fscanf.out", "w+" ) != 0 )  
      printf( "The file fscanf.out was not opened\n" );  
   else  
   {  
      fprintf( stream, "%s %ld %f%c", "a-string",   
               65000, 3.14159, 'x' );  
      // Security caution!  
      // Beware loading data from a file without confirming its size,  
      // as it may lead to a buffer overrun situation.  
  
      // Set pointer to beginning of file:  
      fseek( stream, 0L, SEEK_SET );  
  
      // Read data back from file:  
      fscanf( stream, "%s", s );   // C4996  
      fscanf( stream, "%ld", &l ); // C4996  
  
      fscanf( stream, "%f", &fp ); // C4996  
      fscanf( stream, "%c", &c );  // C4996  
      // Note: fscanf is deprecated; consider using fscanf_s instead  
  
      // Output data read:   
      printf( "%s\n", s );  
      printf( "%ld\n", l );  
      printf( "%f\n", fp );  
      printf( "%c\n", c );  
  
      fclose( stream );  
   }  
}  
```  
  
```Output  
a-string  
65000  
3.141590  
x  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf, _fprintf_l, fwprintf, _fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [scanf, _scanf_l, wscanf, _wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, _sscanf_l, swscanf, _swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)