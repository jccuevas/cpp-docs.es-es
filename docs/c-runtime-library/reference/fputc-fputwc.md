---
title: fputc, fputwc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fputc
- fputwc
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
- fputc
- fputwc
- _fputtc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
caps.latest.revision: 20
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
ms.openlocfilehash: 7eb1bb55bd153f4ef5387b616b72f611e3a50a9f
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="fputc-fputwc"></a>fputc, fputwc
Escribe un carácter en un flujo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int fputc(  
   int c,  
   FILE *stream   
);  
wint_t fputwc(  
   wchar_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Carácter que se va a escribir.  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve el carácter escrito. En el caso de `fputc`, el valor `EOF` devuelto indica un error. En el caso de `fputwc`, el valor `WEOF` devuelto indica un error. Si `stream` es `NULL`, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
 Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas funciones escribe el carácter único `c` en un archivo, en la posición indicada por el indicador de posición de archivo asociado (si está definido) y hace avanzar el indicador según corresponda. En el caso de `fputc` y `fputwc`, está asociado el archivo `stream`. Si el archivo no admite solicitudes de posición o no se abrió en modo Append, el carácter se anexa al final del flujo.  
  
 Las dos funciones se comportan igual si el flujo se abre en modo ANSI. `fputc` no admite actualmente la salida a un flujo UNICODE.  
  
 Las versiones con el sufijo `_nolock` son idénticas, salvo que no están protegidas contra interferencias de otros subprocesos. Para obtener más información, consulte [_fputc_nolock, _fputwc_nolock](../../c-runtime-library/reference/fputc-nolock-fputwc-nolock.md).  
  
 Comentarios específicos de la rutina.  
  
|Rutina|Comentarios|  
|-------------|-------------|  
|`fputc`|Equivale a `putc`, pero implementado solo como función, y no como una función y una macro.|  
|`fputwc`|Versión de caracteres anchos de `fputc`. Escribe `c` como carácter multibyte o carácter ancho en función de que `stream` se haya abierto en modo de texto o modo binario.|  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fputtc`|`fputc`|`fputc`|`fputwc`|  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`fputc`|\<stdio.h>|  
|`fputwc`|\<stdio.h> o \<wchar.h>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_fputc.c  
// This program uses fputc  
// to send a character array to stdout.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char strptr1[] = "This is a test of fputc!!\n";  
   char *p;  
  
   // Print line to stream using fputc.   
   p = strptr1;  
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;  
  
}  
```  
  
```Output  
This is a test of fputc!!  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fgetc, fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)
