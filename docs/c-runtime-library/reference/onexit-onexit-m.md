---
title: _onexit, _onexit_m | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _onexit
- _onexit_m
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
- _onexit
- onexit_m
- onexit
- _onexit_m
dev_langs:
- C++
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 50070672e990333073f5ad7f7ba604110c3a3cfa
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="onexit-onexitm"></a>_onexit, _onexit_m
Registra una rutina que se llama a la hora de salida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_onexit_t _onexit(  
   _onexit_t function  
);  
_onexit_t_m _onexit_m(  
   _onexit_t_m function  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `function`  
 Puntero a una función a la que se va a llamar al salir.  
  
## <a name="return-value"></a>Valor devuelto  
 `_onexit` devuelve un puntero a la función si es correcto o `NULL` si no hay ningún espacio para almacenar el puntero de función.  
  
## <a name="remarks"></a>Comentarios  
 A la función `_onexit` se pasa la dirección de una función (`function`) que se llamará cuando el programa finalice con normalidad. Las llamadas sucesivas a `_onexit` crean un registro de las funciones que se ejecutan por orden de último en entrar, primero en salir (LIFO). Las funciones que se pasan a `_onexit` no pueden tomar parámetros.  
  
 Si se llama a `_onexit` desde un archivo DLL, las rutinas registradas con `_onexit` se ejecutan en un archivo DLL que se descarga después de llamar a `DllMain` con DLL_PROCESS_DETACH.  
  
 `_onexit` es una extensión de Microsoft. Para la portabilidad de ANSI, use [atexit](../../c-runtime-library/reference/atexit.md). La versión `_onexit_m` de la función sirve para el modo mixto.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_onexit`|\<stdlib.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_onexit.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
/* Prototypes */  
int fn1(void), fn2(void), fn3(void), fn4 (void);  
  
int main( void )  
{  
   _onexit( fn1 );  
   _onexit( fn2 );  
   _onexit( fn3 );  
   _onexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
int fn1()  
{  
   printf( "next.\n" );  
   return 0;  
}  
  
int fn2()  
{  
   printf( "executed " );  
   return 0;  
}  
  
int fn3()  
{  
   printf( "is " );  
   return 0;  
}  
  
int fn4()  
{  
   printf( "This " );  
   return 0;  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
This is executed first.  
This is executed next.  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [__dllonexit](../../c-runtime-library/dllonexit.md)
