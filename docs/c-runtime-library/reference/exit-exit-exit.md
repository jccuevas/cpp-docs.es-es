---
title: exit, _Exit, _exit
ms.date: 4/2/2020
api_name:
- _exit
- exit
- _o__exit
- _o_exit
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.openlocfilehash: 5bdb5ff5c8309e03a49f9518f65a45d5757e9bfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347635"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Finaliza el proceso de llamada. La función **exit** la termina después de la limpieza; **_exit** y **_Exit** terminarlo inmediatamente.

> [!NOTE]
> No use este método para cerrar una aplicación de la Plataforma universal de Windows (UWP), excepto en escenarios de prueba o depuración. No se permiten formas de uso mediante programación o de interfaz de usuario para cerrar una aplicación de la Tienda de acuerdo con las directivas de [Microsoft Store.](/legal/windows/agreements/store-policies) Para obtener más información, consulta Ciclo de vida de la [aplicación para UWP](/windows/uwp/launch-resume/app-lifecycle). Para más información sobre las aplicaciones de Windows 10, consulte [Guías de procedimientos para aplicaciones de Windows 10](https://developer.microsoft.com/windows/apps).

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

*status*<br/>
Código de estado de salida.

## <a name="remarks"></a>Observaciones

Las funciones **exit**, **_Exit** y **_exit** finalizan el proceso de llamada. La función **exit** llama a los destructores de objetos locales de subprocesos y, a continuación, llama (en orden de último en entrar y primero en salir (LIFO), a las funciones registradas por **atexit** y _onexit y, **a**continuación, vacía todos los búferes de archivos antes de que finalice el proceso. Las funciones **_Exit** y **_exit** finalizan el proceso sin destruir objetos locales de subprocesos ni procesar funciones **atexit** o **_onexit,** y sin vaciar búferes de flujo.

Aunque las llamadas **exit**, **_Exit** y **_exit** no devuelven un valor, el valor de *status* está disponible para el entorno host o el proceso de llamada en espera, si existe, después de que se cierre el proceso. Normalmente, el autor de la llamada establece el valor de *estado* en 0 para indicar una salida normal o en algún otro valor para indicar un error. El valor de *estado* está disponible para el comando por lotes del sistema operativo **ERRORLEVEL** y se representa mediante una de las dos constantes: **EXIT_SUCCESS**, que representa un valor de 0 o **EXIT_FAILURE**, que representa un valor de 1.

Las funciones **exit**, **_Exit**, **_exit**, **quick_exit**, **_cexit**y **_c_exit** se comportan de la siguiente manera.

|Función|Descripción|
|--------------|-----------------|
|**Salida**|Realiza procedimientos completos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**_Exit**|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**_exit**|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**quick_exit**|Realiza procedimientos rápidos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**_cexit**|Realiza procedimientos completos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|
|**_c_exit**|Realiza procedimientos mínimos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|

Cuando se llama a la función **exit**, **_Exit** o **_exit,** no se llama a los destructores de los objetos temporales o automáticos que existen en el momento de la llamada. Un objeto automático es un objeto local no estático definido en una función. Un objeto temporal es un objeto creado por el compilador, como un valor devuelto por una llamada de función. Para destruir un objeto automático antes de llamar a **exit**, **_Exit**o **_exit**, llame explícitamente al destructor del objeto, como se muestra aquí:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

No utilice **DLL_PROCESS_ATTACH** para llamar a **exit** desde **DllMain**. Para salir de la función **DLLMain,** devuelva **FALSE** desde **DLL_PROCESS_ATTACH**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**salida,** **_Exit**, **_exit**|\<process.h> o \<stdlib.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[Aborta](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec funciones](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, funciones _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
