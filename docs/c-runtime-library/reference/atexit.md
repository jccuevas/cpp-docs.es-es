---
title: atexit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: atexit
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
f1_keywords: atexit
dev_langs: C++
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e812f39041287d17ee87766f6971d299654f0f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atexit"></a>atexit
Procesa la función especificada a la salida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int atexit(  
   void (__cdecl *func )( void )  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `func`  
 Función a la que se llama.  
  
## <a name="return-value"></a>Valor devuelto  
 `atexit` devuelve 0 si se ejecuta correctamente, o un valor distinto de cero si se produce un error.  
  
## <a name="remarks"></a>Comentarios  
 A la función `atexit` se pasa la dirección de una función (`func`) que se llamará cuando el programa finalice con normalidad. Las llamadas sucesivas a `atexit` crean un registro de las funciones que se ejecutan por orden de último en entrar, primero en salir (LIFO). Las funciones que se pasan a `atexit` no pueden tomar parámetros. `atexit` y `_onexit` usan el montón para almacenar el registro de funciones. Por lo tanto, el número de funciones que se pueden registrar no tiene más límite que la memoria del montón.  
  
 El código de la función `atexit` no debe contener ninguna dependencia de ningún archivo DLL que pueda haberse descargado ya cuando se llama a la función `atexit`.  
  
 Para generar una aplicación compatible con ANSI, use la función estándar ANSI `atexit` (y no la función similar `_onexit`).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`atexit`|\<stdlib.h>|  
  
## <a name="example"></a>Ejemplo  
 Este programa inserta cuatro funciones en la pila de funciones que se ejecuta al llamar a `atexit`. Cuando el programa termina, estos programas se ejecutan por último en entrar, primero en salir.  
  
```  
// crt_atexit.c  
#include <stdlib.h>  
#include <stdio.h>  
  
void fn1( void ), fn2( void ), fn3( void ), fn4( void );  
  
int main( void )  
{  
   atexit( fn1 );  
   atexit( fn2 );  
   atexit( fn3 );  
   atexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
void fn1()  
{  
   printf( "next.\n" );  
}  
  
void fn2()  
{  
   printf( "executed " );  
}  
  
void fn3()  
{  
   printf( "is " );  
}  
  
void fn4()  
{  
   printf( "This " );  
}  
```  
  
```Output  
This is executed first.  
This is executed next.  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)