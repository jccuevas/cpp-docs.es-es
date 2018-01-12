---
title: memmove_s, wmemmove_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wmemmove_s
- memmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wmemmove_s
- memmove_s
dev_langs: C++
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8194acf1a8a0708d2584745a7a49449ca7f554c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="memmoves-wmemmoves"></a>memmove_s, wmemmove_s
Mueve un búfer a otro. Se trata de versiones de [memmove, wmemmove](../../c-runtime-library/reference/memmove-wmemmove.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      errno_t memmove_s(  
   void *dest,  
   size_t numberOfElements,  
   const void *src,  
   size_t count  
);  
errno_t wmemmove_s(  
   wchar_t *dest,  
   size_t numberOfElements,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dest`  
 Objeto de destino.  
  
 `numberOfElements`  
 Tamaño del búfer de destino.  
  
 `src`  
 Objeto de origen.  
  
 `count`  
 Número de bytes (`memmove_s`) o caracteres (`wmemmove_s`) que se copiarán.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`dest`|`numberOfElements`|`src`|Valor devuelto|Contenido de `dest`|  
|------------|------------------------|-----------|------------------|------------------------|  
|`NULL`|any|any|`EINVAL`|no modificado|  
|any|any|`NULL`|`EINVAL`|no modificado|  
|any|< `count`|any|`ERANGE`|no modificado|  
  
## <a name="remarks"></a>Comentarios  
 Copias `count` bytes de caracteres de `src` a `dest`. Si algunas regiones del área de origen y del destino se superponen, `memmove_s` se asegura de que se copian los bytes de origen originales en la región superpuesta antes de que se sobrescriban.  
  
 Si `dest` o `src` es un puntero nulo, o si la cadena de destino es demasiado pequeña, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven `EINVAL` y establecen `errno` en `EINVAL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`memmove_s`|\<string.h>|  
|`wmemmove_s`|\<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_memmove_s.c  
//  
// The program demonstrates the   
// memmove_s function which works as expected  
// for moving overlapping regions.  
  
#include <stdio.h>  
#include <string.h>  
  
int main()  
{  
   char str[] = "0123456789";  
  
   printf("Before: %s\n", str);  
  
   // Move six bytes from the start of the string  
   // to a new position shifted by one byte. To protect against  
   // buffer overrun, the secure version of memmove requires the  
   // the length of the destination string to be specified.   
  
   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);   
  
   printf_s(" After: %s\n", str);  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
Before: 0123456789  
 After: 0012345789  
```  
  
## <a name="see-also"></a>Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memcpy, wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [strcpy_s, wcscpy_s, _mbscpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strcpy, wcscpy, _mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)