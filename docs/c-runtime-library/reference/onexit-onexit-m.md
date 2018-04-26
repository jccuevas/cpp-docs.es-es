---
title: _onexit, _onexit_m | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: ac59e64c1e47d699170af772aeba60a7895dfdc2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="onexit-onexitm"></a>_onexit, _onexit_m

Registra una rutina que se llama a la hora de salida.

## <a name="syntax"></a>Sintaxis

```C
_onexit_t _onexit(
   _onexit_t function
);
_onexit_t_m _onexit_m(
   _onexit_t_m function
);
```

### <a name="parameters"></a>Parámetros

*function*<br/>
Puntero a una función a la que se va a llamar al salir.

## <a name="return-value"></a>Valor devuelto

**_onexit** devuelve un puntero a la función si se realiza correctamente o **NULL** si no hay ningún espacio para almacenar el puntero de función.

## <a name="remarks"></a>Comentarios

El **_onexit** función se le pasa la dirección de una función (*función*) que se llamará cuando el programa finaliza con normalidad. Las llamadas sucesivas a **_onexit** crea un registro de las funciones que se ejecutan en orden LIFO (último en-primero en salir). Las funciones que se pasan a **_onexit** no pueden tomar parámetros.

En el caso cuando **_onexit** se llama desde dentro de un archivo DLL, rutinas registradas con **_onexit** ejecución en un archivo DLL de la descarga después de **DllMain** se llama con DLL_PROCESS_DETACH.

**_onexit** es una extensión de Microsoft. Para la portabilidad de ANSI, use [atexit](atexit.md). El **_onexit_m** versión de la función es para uso de modo mixto.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
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

### <a name="output"></a>Salida

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
