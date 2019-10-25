---
title: atexit
ms.date: 11/04/2016
api_name:
- atexit
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
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: b91e6dad81f006b0b94ac17a940e840386f6d2b1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939656"
---
# <a name="atexit"></a>atexit

Procesa la función especificada a la salida.

## <a name="syntax"></a>Sintaxis

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>Parámetros

*func*<br/>
Función a la que se llama.

## <a name="return-value"></a>Valor devuelto

**AtExit** devuelve 0 si se realiza correctamente, o un valor distinto de cero si se produce un error.

## <a name="remarks"></a>Comentarios

A la función **AtExit** se le pasa la dirección de una función *FUNC* a la que se llamará cuando el programa finalice con normalidad. Las llamadas sucesivas a **AtExit** crean un registro de las funciones que se ejecutan en el orden LIFO (último en salir, primero en salir). Las funciones pasadas a **AtExit** no pueden tomar parámetros. **AtExit** y **_onexit** usan el montón para contener el registro de funciones. Por lo tanto, el número de funciones que se pueden registrar no tiene más límite que la memoria del montón.

El código de la función **AtExit** no debe contener ninguna dependencia de ningún archivo DLL que pueda haberse descargado ya cuando se llama a la función **AtExit** .

Para generar una aplicación compatible con ANSI, utilice la función **AtExit** de ANSI-Standard (en lugar de la función **_onexit** similar).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>Ejemplo

Este programa envía cuatro funciones a la pila de funciones que se van a ejecutar cuando se llama a **AtExit** . Cuando el programa termina, estos programas se ejecutan por último en entrar, primero en salir.

```C
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

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
