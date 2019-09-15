---
title: _onexit, _onexit_m
ms.date: 11/04/2016
api_name:
- _onexit
- _onexit_m
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _onexit
- onexit_m
- onexit
- _onexit_m
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
ms.openlocfilehash: 9afcd729f19f11b82e8f24c2b7fcf9ec40990deb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951343"
---
# <a name="_onexit-_onexit_m"></a>_onexit, _onexit_m

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

**_onexit** devuelve un puntero a la función si se realiza correctamente o **null** si no hay ningún espacio para almacenar el puntero de función.

## <a name="remarks"></a>Comentarios

A la función **_onexit** se le pasa la dirección de una función (*function*) a la que se llamará cuando el programa finalice con normalidad. Las llamadas sucesivas a **_onexit** crean un registro de las funciones que se ejecutan en el orden LIFO (último en salir). Las funciones pasadas a **_onexit** no pueden tomar parámetros.

En el caso de que se llame a **_onexit** desde un archivo dll, las rutinas registradas con **_onexit** se ejecutan en la descarga de un archivo dll una vez que se llama a **DllMain** con DLL_PROCESS_DETACH.

**_onexit** es una extensión de Microsoft. Para la portabilidad de ANSI, use [atexit](atexit.md). La versión **_onexit_m** de la función es para el uso del modo mixto.

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

### <a name="output"></a>Resultados

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
