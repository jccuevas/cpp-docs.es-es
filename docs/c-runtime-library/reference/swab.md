---
title: _swab | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _swab
- stdlib/_swab
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
dev_langs:
- C++
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: a3043abf425055d8cb21108a30db2e6382e19c1a
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="swab"></a>_swab
Intercambia los bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _swab(  
   char *src,  
   char *dest,  
   int n   
);  
```  
  
## <a name="parameters"></a>Parámetros  
 `src`  
 Datos que se van a copiar e intercambiar.  
  
 `dest`  
 Ubicación de almacenamiento de los datos intercambiados.  
  
 `n`  
 Número de bytes que se van a copiar e intercambiar.  
  
## <a name="return-value"></a>Valor devuelto
 La función `swab` no devuelve ningún valor. La función establece `errno` en `EINVAL` si el puntero `src` o `dest` es nulo o si `n` es inferior a cero y se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.
 
## <a name="remarks"></a>Comentarios  
 Si `n` es par, la función `_swab` copia `n` bytes de `src`, intercambia cada par de bytes contiguos y almacena el resultado en `dest`. Si `n` es impar, `_swab` copia e intercambia los primeros `n-1` bytes de `src`, pero no se copia el byte final. La función `_swab` se suele usar para preparar los datos binarios para transferirlos a un equipo que usa un orden de bytes diferente.  
  
## <a name="requirements"></a>Requisitos  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_swab`|C: \<stdlib.h> C++: \<cstdlib> o \<stdlib.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
```C 
// crt_swab.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";  
char to[] =   "...........................";  
  
int main()  
{  
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);  
    _swab(from, to, sizeof(from));  
    printf("After:  %s\n        %s\n\n", from, to);  
}  
```  
  
```Output  
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes  
        ...........................  
  
After:  BADCFEHGJILKNMPORQTSVUXWZY  
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.  
```  
  
## <a name="see-also"></a>Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)
