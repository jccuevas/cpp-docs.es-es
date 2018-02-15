---
title: exit, _Exit, _exit | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _exit
- exit
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed4835662a53f3cb19b47818a9d6adfb3dfb2930
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

Finaliza el proceso de llamada. La función `exit` lo finaliza después de la limpieza; `_exit` y `_Exit` lo finalizan inmediatamente.

> [!NOTE]
> No utilice este método para cerrar una aplicación de plataforma Universal de Windows (UWP), excepto en pruebas o en escenarios de depuración. No se permiten formas mediante programación o la interfaz de usuario para cerrar una aplicación de tienda según la [las directivas de Microsoft Store](/legal/windows/agreements/store-policies). Para obtener más información, consulte [ciclo de vida de aplicación de UWP](/windows/uwp/launch-resume/app-lifecycle). Para más información sobre las aplicaciones de Windows 10, consulte [Guías de procedimientos para aplicaciones de Windows 10](http://go.microsoft.com/fwlink/p/?linkid=619133).

## <a name="syntax"></a>Sintaxis

```C
void exit(
   int const status
);
void _Exit(
   int const status
);
void _exit( 
   int const status
);
```

### <a name="parameters"></a>Parámetros

_status_  
Código de estado de salida.

## <a name="remarks"></a>Comentarios

Las funciones `exit`, `_Exit` y `_exit` finalizan el proceso que realiza la llamada. La función `exit` llama a destructores para los objetos locales para el subproceso y, después, llama (en orden LIFO, donde el último en entrar es primero en salir) a las funciones registradas por `atexit` y `_onexit`para, a continuación, vaciar todos los búferes de archivo antes de finalizar el proceso. Las funciones `_Exit` y `_exit` finalizan el proceso sin destruir objetos locales para el subproceso ni procesar funciones `atexit` o `_onexit` y sin vaciar los búferes de secuencia.

Aunque la `exit`, `_Exit` y `_exit` llamadas no devuelven un valor, el valor de _estado_ estará disponible para el entorno de host o el proceso de llamada en espera, si la hay, al salir del proceso. Normalmente, el llamador establece el _estado_ valor en 0 para indicar una salida normal o a algún otro valor para indicar un error. El _estado_ valor está disponible para el comando por lotes del sistema operativo `ERRORLEVEL` y se representa mediante uno de dos constantes: `EXIT_SUCCESS`, que representa un valor de 0, o `EXIT_FAILURE`, que representa un valor de 1.

Las funciones `exit`, `_Exit`, `_exit`, `quick_exit`, `_cexit`y `_c_exit` se comportan como sigue.

|Función|Descripción|
|--------------|-----------------|
|`exit`|Realiza procedimientos completos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|`_Exit`|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|`_exit`|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|`quick_exit`|Realiza procedimientos rápidos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|`_cexit`|Realiza procedimientos completos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|
|`_c_exit`|Realiza procedimientos mínimos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|

Cuando se llama a la función `exit`,  `_Exit` o `_exit` , no se llama a los destructores de ningún objeto temporal o automático que exista en el momento de la llamada. Un objeto automático es un objeto local no estático definido en una función. Un objeto temporal es un objeto creado por el compilador, como un valor devuelto por una llamada de función. Para destruir un objeto automático antes de llamar a `exit`, `_Exit`, o `_exit`, explícitamente llame al destructor del objeto, como se muestra aquí:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

No use `DLL_PROCESS_ATTACH` para llamar a `exit` desde `DllMain`. Para salir del `DLLMain` funcionar, devolver `FALSE` de `DLL_PROCESS_ATTACH`.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|`exit`, `_Exit`, `_exit`|\<process.h> o \<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_exit.c
// This program returns an exit code of 1. The
// error code could be tested in a batch file.

#include <stdlib.h>

int main( void )
{
   exit( 1 );
}
```

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[atexit](../../c-runtime-library/reference/atexit.md)  
[_cexit, _c_exit](../../c-runtime-library/reference/cexit-c-exit.md)  
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)  
[_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)  
[quick_exit](../../c-runtime-library/reference/quick-exit1.md)  
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)  
[system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)  
