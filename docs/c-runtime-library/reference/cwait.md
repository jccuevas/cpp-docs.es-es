---
title: _cwait
ms.date: 4/2/2020
api_name:
- _cwait
- _o__cwait
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
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: d54f62c8ce391b2c8ead92a0a73ac48e6f2b3cb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348147"
---
# <a name="_cwait"></a>_cwait

Espera hasta que finaliza otro proceso.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
intptr_t _cwait(
   int *termstat,
   intptr_t procHandle,
   int action
);
```

### <a name="parameters"></a>Parámetros

*termstat*<br/>
Puntero a un búfer donde se almacenará el código de resultado del proceso especificado, o **NULL**.

*procHandle*<br/>
El identificador del proceso que se va a esperar (es decir, el proceso que tiene que finalizar antes de **que _cwait** pueda devolver).

*action*<br/>
NULL: ignorado por las aplicaciones del sistema operativo Windows; para otras aplicaciones: código de acción para realizar en *procHandle*.

## <a name="return-value"></a>Valor devuelto

Cuando el proceso especificado se ha completado correctamente, devuelve el identificador del proceso especificado y establece *termstat* en el código de resultado devuelto por el proceso especificado. De lo contrario, devuelve -1 y establece **errno** de la siguiente manera.

|Value|Descripción|
|-----------|-----------------|
|**ECHILD**|No existe ningún proceso especificado, *procHandle* no es válido o se produjo un error en la llamada a la API [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) o [WaitForSingleObject.](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)|
|**EINVAL**|*acción* no es válida.|

Para más información sobre estos y otros códigos devueltos, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_cwait** espera la terminación del identificador de proceso del proceso especificado proporcionado por *procHandle*. El valor de *procHandle* que se pasa a **_cwait** debe ser el valor devuelto por la llamada a la función [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) que creó el proceso especificado. Si el identificador de proceso finaliza antes de que se llame **a _cwait,** **_cwait** devuelve inmediatamente. **_cwait** puede ser utilizado por cualquier proceso para esperar cualquier otro proceso conocido para el que existe un identificador válido (*procHandle*).

*termstat* apunta a un búfer donde se almacenará el código de retorno del proceso especificado. El valor de *termstat* indica si el proceso especificado terminó normalmente llamando a la API [ExitProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) de Windows. **ExitProcess** se llama internamente si las llamadas de proceso especificadas **salen** o **_exit**, devuelven desde **main**o alcanzan el final de **main**. Para obtener más información sobre el valor que se devuelve a través de *termstat*, vea [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Si se llama **a _cwait** mediante un valor **NULL** para *termstat*, no se almacena el código de retorno del proceso especificado.

El sistema operativo Windows omite el parámetro *action* porque las relaciones primario-secundario no se implementan en estos entornos.

A menos que *procHandle* sea -1 o -2 (controla el proceso o subproceso actual), el identificador se cerrará. Por consiguiente, en esta situación, no se debe usar el identificador devuelto.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_cwait.c
// compile with: /c
// This program launches several processes and waits
// for a specified process to finish.

#define _CRT_RAND_S

#include <windows.h>
#include <process.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>

// Macro to get a random integer within a specified range
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))

struct PROCESS
{
   int     nPid;
   char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main( int argc, char *argv[] )
{
   int termstat, c;
   unsigned int number;

   srand( (unsigned)time( NULL ) );    // Seed randomizer

   // If no arguments, this is the calling process
   if ( argc == 1 )
   {
      // Spawn processes in numeric order
      for ( c = 0; c < 4; c++ ) {
         _flushall();
         process[c].nPid = _spawnl( _P_NOWAIT, argv[0], argv[0],
                                    process[c].name, NULL );
      }

      // Wait for randomly specified process, and respond when done
      c = getrandom( 0, 3 );
      printf( "Come here, %s.\n", process[c].name );
      _cwait( &termstat, process[c].nPid, _WAIT_CHILD );
      printf( "Thank you, %s.\n", process[c].name );

   }
   // If there are arguments, this must be a spawned process
   else
   {
      // Delay for a period that's determined by process number
      Sleep( (argv[1][0] - 'A' + 1) * 1000L );
      printf( "Hi, Dad. It's %s.\n", argv[1] );
   }
}
```

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>Consulte también

[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, funciones _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
