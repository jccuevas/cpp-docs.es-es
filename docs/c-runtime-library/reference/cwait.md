---
title: _cwait | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _cwait
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cwait
dev_langs:
- C++
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 878c1c08dabe52a31a2bdf377c3e0bb167a9ae5d
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="cwait"></a>_cwait

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
El identificador del proceso que esperar (es decir, el proceso que tiene que finalizar antes **_cwait** puede devolver).

*Acción*<br/>
NULL: Omite las aplicaciones del sistema operativo de Windows; para otras aplicaciones: código de acción para llevar a cabo en *procHandle*.

## <a name="return-value"></a>Valor devuelto

Cuando se haya completado correctamente el proceso especificado, devuelve el identificador del proceso especificado y establece *termstat* en el código de resultado devuelto por el proceso especificado. En caso contrario, devuelve -1 y establece **errno** como se indica a continuación.

|Valor|Descripción|
|-----------|-----------------|
|**ECHILD**|No existe ningún proceso especificado, *procHandle* no es válido o la llamada a la [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx) o [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx) error de la API.|
|**EINVAL**|*acción* no es válido.|

Para obtener más información sobre estos y otros códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_cwait** función espera la finalización de la Id. de proceso del proceso especificado que proporciona *procHandle*. El valor de *procHandle* que se pasa a **_cwait** debería ser el valor devuelto por la llamada a la [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) función que creó el proceso especificado. Si el identificador de proceso termina antes de **_cwait** se llama, **_cwait** devuelve inmediatamente. **_cwait** puede usar en cualquier proceso para esperar a cualquier otro proceso conocido para el que un identificador válido (*procHandle*) existe.

*termstat* apunta a un búfer donde se almacenará el código de retorno del proceso especificado. El valor de *termstat* indica si el proceso especificado terminó con normalidad mediante una llamada a las ventanas [ExitProcess](http://msdn.microsoft.com/library/windows/desktop/ms682658.aspx) API. **ExitProcess** llama internamente si el proceso especificado llama **salir** o **_exit**, devuelve de **principal**, o llega al final de **principal** . Para obtener más información acerca del valor que se pasa a través de *termstat*, consulte [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx). Si **_cwait** llamar mediante un **NULL** valor *termstat*, no se almacena el código de retorno del proceso especificado.

El *acción* parámetro se ignora por el sistema operativo Windows, porque las relaciones de elementos primarios y secundarios no se implementan en estos entornos.

A menos que *procHandle* es -1 o -2 (identificadores para el proceso actual o el subproceso), el identificador se cierra. Por consiguiente, en esta situación, no se debe usar el identificador devuelto.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
