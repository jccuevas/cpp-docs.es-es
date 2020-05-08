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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a1c0eeaa6d66e91b913ce7940d37409fc4f6ac29
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909668"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Finaliza el proceso de llamada. La función **Exit** lo finaliza después de la limpieza; **_exit** y **_Exit** terminan inmediatamente.

> [!NOTE]
> No use este método para cerrar una aplicación Plataforma universal de Windows (UWP), excepto en escenarios de prueba o depuración. No se permiten las formas de cerrar una aplicación de la tienda mediante programación o la interfaz de usuario de acuerdo con las [directivas de Microsoft Store](/legal/windows/agreements/store-policies). Para obtener más información, consulte el ciclo de vida de las [aplicaciones para UWP](/windows/uwp/launch-resume/app-lifecycle). Para más información sobre las aplicaciones de Windows 10, consulte [Guías de procedimientos para aplicaciones de Windows 10](https://developer.microsoft.com/windows/apps).

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

Las funciones **Exit**, **_Exit** y **_exit** finalizan el proceso de llamada. La función **Exit** llama a destructores para los objetos locales de subproceso y, a continuación, llama a, en orden LIFO (último en salir), las funciones que se registran en **AtExit** y **_onexit**y, a continuación, vacía todos los búferes de archivo antes de finalizar el proceso. Las funciones **_Exit** y **_exit** finalizan el proceso sin destruir objetos locales para el subproceso ni procesar funciones **AtExit** o **_onexit** y sin vaciar los búferes de secuencia.

Aunque las llamadas de **salida**, **_Exit** y **_exit** no devuelven un valor, el valor de *status* está disponible para el entorno de host o el proceso de llamada en espera, en caso de que exista uno, una vez finalizado el proceso. Normalmente, el autor de la llamada establece el valor de *Estado* en 0 para indicar una salida normal, o en algún otro valor para indicar un error. El valor de *Estado* está disponible para el comando de proceso por lotes del sistema operativo **ERRORLEVEL** y se representa mediante una de dos constantes: **EXIT_SUCCESS**, que representa un valor de 0, o **EXIT_FAILURE**, que representa un valor de 1.

Las funciones de **salida**, **_Exit**, **_exit**, **quick_exit**, **_cexit**y **_c_exit** se comportan como se indica a continuación.

|Función|Descripción|
|--------------|-----------------|
|**exit**|Realiza procedimientos completos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**_Exit**|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**_exit**|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**quick_exit**|Realiza procedimientos rápidos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**_cexit**|Realiza procedimientos completos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|
|**_c_exit**|Realiza procedimientos mínimos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|

Cuando se llama a la función **Exit**, **_Exit** o **_exit** , no se llama a los destructores de ningún objeto temporal o automático que exista en el momento de la llamada. Un objeto automático es un objeto local no estático definido en una función. Un objeto temporal es un objeto creado por el compilador, como un valor devuelto por una llamada de función. Para destruir un objeto automático antes de llamar a **Exit**, **_Exit**o **_exit**, llame explícitamente al destructor del objeto, como se muestra aquí:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

No utilice **DLL_PROCESS_ATTACH** para llamar a **Exit** desde **DllMain**. Para salir de la función **DllMain** , devuelva **false** desde **DLL_PROCESS_ATTACH**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**salir**, **_Exit** **_exit**|\<process.h> o \<stdlib.h>|

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

[Control de proceso y entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[aborta](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec funciones](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn funciones](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
