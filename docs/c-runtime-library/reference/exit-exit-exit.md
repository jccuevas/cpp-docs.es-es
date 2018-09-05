---
title: exit, _Exit, _exit | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
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
ms.workload:
- cplusplus
ms.openlocfilehash: 8a06fa858ac7d2d8458bd3adf3fb44ca7bdee929
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678159"
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

Finaliza el proceso de llamada. El **salir** función lo finaliza después de la limpieza; **_exit** y **_Exit** lo finalizan inmediatamente.

> [!NOTE]
> No utilice este método para cerrar una aplicación plataforma Universal de Windows (UWP), excepto en las pruebas o escenarios de depuración. No se permiten formas mediante programación o con la interfaz de usuario para cerrar una aplicación de Store según la [las directivas de Microsoft Store](/legal/windows/agreements/store-policies). Para obtener más información, consulte [ciclo de vida de aplicación para UWP](/windows/uwp/launch-resume/app-lifecycle). Para más información sobre las aplicaciones de Windows 10, consulte [Guías de procedimientos para aplicaciones de Windows 10](https://developer.microsoft.com/en-us/windows/apps).

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

*estado* código de estado de salida.

## <a name="remarks"></a>Comentarios

El **salir**, **_Exit** y **_exit** funciones terminan el proceso de llamada. El **salir** función llama a destructores para objetos de subproceso local, a continuación, llama a, en orden de último en el primero en salir (LIFO), las funciones registradas por **atexit** y **_onexit**y, a continuación, vacía todos los búferes de archivo antes de finalizar el proceso. El **_Exit** y **_exit** funciones finalizan el proceso sin destruir objetos locales de subproceso ni procesar **atexit** o **_onexit**funciones y sin vaciar los búferes de secuencia.

Aunque el **salir**, **_Exit** y **_exit** llamadas no devuelven un valor, el valor en *estado* está disponible para el entorno de host o proceso que realiza la llamada, en espera si la hay, al salir del proceso. Normalmente, el llamador establece el *estado* valor en 0 para indicar una salida normal o a algún otro valor para indicar un error. El *estado* valor está disponible para el comando por lotes del sistema operativo **ERRORLEVEL** y se representa mediante uno de dos constantes: **EXIT_SUCCESS**, que representa un valor de 0, o **EXIT_FAILURE**, que representa un valor de 1.

El **salir**, **_Exit**, **_exit**, **quick_exit**, **_cexit**, y **_c_exit** funciones se comportan como sigue.

|Función|Descripción|
|--------------|-----------------|
|**exit**|Realiza procedimientos completos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**_Exit**|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**_exit**|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**quick_exit**|Realiza procedimientos rápidos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|
|**_cexit**|Realiza procedimientos completos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|
|**_c_exit**|Realiza procedimientos mínimos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|

Cuando se llama a la **salir**, **_Exit** o **_exit** función, no se llaman a los destructores de ningún objeto temporal o automático que exista en el momento de la llamada. Un objeto automático es un objeto local que no sea estático definido en una función. Un objeto temporal es un objeto creado por el compilador, como un valor devuelto por una llamada de función. Para destruir un objeto automático antes de llamar a **salir**, **_Exit**, o **_exit**explícitamente llame al destructor del objeto, como se muestra aquí:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

No use **DLL_PROCESS_ATTACH** para llamar a **salir** desde **DllMain**. Para salir del **DLLMain** de función, devolver **FALSE** desde **DLL_PROCESS_ATTACH**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**salir**, **_Exit**, **_exit**|\<process.h> o \<stdlib.h>|

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

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
