---
title: atexit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- atexit
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
- atexit
dev_langs:
- C++
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d66954348d5d812fac7eca0b231304267cc26157
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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

*Func*<br/>
Función a la que se llama.

## <a name="return-value"></a>Valor devuelto

**atexit** devuelve 0 si se realiza correctamente, o un valor distinto de cero si se produce un error.

## <a name="remarks"></a>Comentarios

El **atexit** función se le pasa la dirección de una función *func* se llama cuando el programa finaliza con normalidad. Las llamadas sucesivas a **atexit** crea un registro de las funciones que se ejecutan en orden, último en salir (LIFO). Las funciones que se pasan a **atexit** no pueden tomar parámetros. **atexit** y **_onexit** utilizar el montón para almacenar el registro de funciones. Por lo tanto, el número de funciones que se pueden registrar no tiene más límite que la memoria del montón.

El código en el **atexit** función no puede contener cualquier dependencia de cualquier archivo DLL que podría haber ya se ha descargado cuando el **atexit** función se invoca.

Para generar una aplicación compatible con ANSI, use el estándar ANSI **atexit** función (en lugar de la similar **_onexit** función).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>Ejemplo

Este programa inserciones cuatro funciones en la pila de funciones que se ejecute cuando **atexit** se llama. Cuando el programa termina, estos programas se ejecutan por último en entrar, primero en salir.

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
