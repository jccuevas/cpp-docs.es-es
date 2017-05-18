---
title: ungetc, ungetwc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ungetwc
- ungetc
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ungettc
- ungetwc
- ungetc
dev_langs:
- C++
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 3bab0bd81a8a17fd32c244bab0dd30658564d257
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc
Vuelve a insertar un carácter en el flujo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int ungetc(  
   int c,  
   FILE *stream   
);  
wint_t ungetwc(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Carácter que se va a devolver.  
  
 `stream`  
 Puntero a la estructura `FILE` .  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, cada una de estas funciones devuelve el argumento de carácter `c`. Si `c` no se puede volver a insertar o si no se ha leído ningún carácter, el flujo de entrada no cambia y `ungetc` devuelve `EOF`; `ungetwc` devuelve `WEOF`. Si `stream` es `NULL`, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, se devuelve `EOF` o `WEOF` y `errno` se establece en `EINVAL`.  
  
 Para más información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `ungetc` vuelve a insertar el carácter `c` en `stream` y borra el indicador de fin de archivo. El flujo debe estar abierto para lectura. Siguiente operación de lectura en `stream` comienza con `c`. Los intentos de insertar `EOF` en el flujo mediante `ungetc` se omiten.  
  
 Los caracteres que `ungetc` pone en el flujo se podrían borrar si se llama a `fflush`, `fseek`, `fsetpos` o `rewind` antes de que se lea el carácter del flujo. El indicador de posición de archivo tendrá el valor que tenía antes de que se volvieran a insertar los caracteres. El almacenamiento externo correspondiente al flujo no cambia. Si una llamada de `ungetc` en un flujo de texto se realiza correctamente, el indicador de posición del archivo está sin especificar hasta que se leen o se descarten todos los caracteres que se han vuelto a insertar. En cada llamada correcta de `ungetc` en un flujo binario se reduce el indicador de posición de archivo. Si el valor era 0 antes de una llamada, el valor queda sin definir después de la llamada.  
  
 Los resultados son imprevisibles si se llama a `ungetc` dos veces sin que haya una operación de lectura o de posición de archivo entre las dos llamadas. Después de una llamada a `fscanf`, una llamada a `ungetc` puede generar un error a menos que se haya realizado otra operación de lectura (por ejemplo `getc`). La razón es que la función `fscanf` ya llama a `ungetc`.  
  
 `ungetwc` es una versión con caracteres anchos de `ungetc`. Sin embargo, en cada llamada correcta de `ungetwc` en un flujo de texto o binario, el valor del indicador de posición de archivo no se especifica hasta que se leen o se descartan todos los caracteres que se han vuelto a insertar.  
  
 Estas funciones son seguras para subprocesos y bloquean los datos confidenciales durante la ejecución. Para obtener una versión que no es de bloqueo, vea [_ungetc_nolock, _ungetwc_nolock](../../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ungettc`|`ungetc`|`ungetc`|`ungetwc`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`ungetc`|\<stdio.h>|  
|`ungetwc`|\<stdio.h> o \<wchar.h>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_ungetc.c  
// This program first converts a character  
// representation of an unsigned integer to an integer. If  
// the program encounters a character that is not a digit,  
// the program uses ungetc to replace it in the  stream.  
//  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   int result = 0;  
  
   // Read in and convert number:  
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )  
      result = result * 10 + ch - '0';    // Use digit.  
   if( ch != EOF )  
      ungetc( ch, stdin );                // Put nondigit back.  
   printf( "Number = %d\nNext character in stream = '%c'",   
            result, getchar() );  
}  
```  
  
```Output  
  
      521aNumber = 521  
Next character in stream = 'a'  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)
