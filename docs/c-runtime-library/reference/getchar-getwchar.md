---
title: getchar, getwchar | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- getchar
- getwchar
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
- getwchar
- GetChar
dev_langs:
- C++
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2e3af8fbc613a3c1634e24011e22283dd8520f7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="getchar-getwchar"></a>getchar, getwchar
Lee un carácter de entrada estándar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int getchar();  
wint_t getwchar();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el carácter leído. Para indicar un error de lectura o una condición de final de archivo, `getchar` devuelve `EOF` y `getwchar` devuelve `WEOF`. En el caso de `getchar`, use `ferror` o `feof` para comprobar si hay un error o una condición de fin de archivo.  
  
## <a name="remarks"></a>Comentarios  
 Cada rutina lee un solo carácter de `stdin` y aumenta el puntero de archivo asociado para que señale al carácter siguiente. `getchar` es igual que [_fgetchar](../../c-runtime-library/reference/fgetc-fgetwc.md), pero se implementa como función y como macro.  
  
 Estas funciones bloquean el subproceso de llamada y son, por consiguiente, seguras para subprocesos. Para obtener una versión que no sea de bloqueo, consulte [_getchar_nolock, _getwchar_nolock](../../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_gettchar`|`getchar`|`getchar`|`getwchar`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`getchar`|\<stdio.h>|  
|`getwchar`|\<stdio.h> o \<wchar.h>|  
  
La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola, `stdin`, `stdout`, y `stderr`, se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_getchar.c  
// Use getchar to read a line from stdin.  
  
#include <stdio.h>  
  
int main()  
{  
    char buffer[81];  
    int i, ch;  
  
    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)  
                         && (ch != '\n'); i++)  
    {  
        buffer[i] = (char) ch;  
    }  
  
    // Terminate string with a null character   
    buffer[i] = '\0';  
    printf( "Input was: %s\n", buffer);  
}  
```  
  
```Output  
  
This textInput was: This text  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [fgetc, fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)   
 [_getch, _getwch](../../c-runtime-library/reference/getch-getwch.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)   
 [ungetc, ungetwc](../../c-runtime-library/reference/ungetc-ungetwc.md)