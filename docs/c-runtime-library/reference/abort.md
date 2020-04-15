---
title: anular
ms.date: 4/2/2020
api_name:
- abort
- _o_abort
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
- Abort
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.openlocfilehash: 1f70f54783ce6f6d28fdda028af4fd5a205aeb0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350927"
---
# <a name="abort"></a>anular

Anula el proceso actual y devuelve un código de error.

> [!NOTE]
> No uses este método para cerrar una aplicación de Microsoft Store o una aplicación de la Plataforma universal de Windows (UWP), excepto en escenarios de prueba o depuración. No se permiten formas de uso mediante programación o de interfaz de usuario para cerrar una aplicación de la Tienda de acuerdo con las directivas de [Microsoft Store.](/legal/windows/agreements/store-policies) Para obtener más información, consulta Ciclo de vida de la [aplicación para UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Sintaxis

```C
void abort( void );
```

## <a name="return-value"></a>Valor devuelto

**anular** no devuelve el control al proceso de llamada. De forma predeterminada, busca un controlador de señales de anulación y genera `SIGABRT` si se ha establecido uno. A **continuación, abortar** finaliza el proceso actual y devuelve un código de salida al proceso primario.

## <a name="remarks"></a>Observaciones

**Microsoft Specific**

De forma predeterminada, cuando se compila una aplicación con la biblioteca `SIGABRT` en tiempo de ejecución de depuración, la rutina de **anulación** muestra un mensaje de error antes de que se genere. En el caso de aplicaciones de consola que se ejecuten en modo de consola, el mensaje se envía a `STDERR`. Las aplicaciones de escritorio de Windows y las aplicaciones de consola que se ejecutan en modo de ventana muestran el mensaje en un cuadro de mensaje. Para suprimir el mensaje, use [_set_abort_behavior](set-abort-behavior.md) para borrar la marca `_WRITE_ABORT_MSG`. El mensaje que aparece depende de la versión del entorno en tiempo de ejecución que se use. Para las aplicaciones creadas mediante las versiones más recientes de Visual C++, el mensaje se asemeja a esto:

> R6010 - abort() ha sido llamado

En versiones anteriores de la biblioteca en tiempo de ejecución de C, se muestra este mensaje:

> Esta aplicación solicitó la finalización del tiempo de ejecución de modo no habitual. Póngase en contacto con el equipo de asistencia técnica de la aplicación para obtener más información.

Cuando el programa se compila en modo de depuración, el cuadro de mensaje muestra opciones para **Anular**, **Reintentar** u **Omitir**. Si el usuario elige **Anular**, el programa finaliza inmediatamente y devuelve un código de salida de 3. Si el usuario elige **Reintentar**, se invoca a un depurador para la depuración Just-In-Time, si está disponible. Si el usuario elige **Ignorar**, **abortar** continúa el procesamiento normal.

En las compilaciones comerciales y de depuración, **abortar** comprueba si se ha establecido un controlador de señal de anulación. Si se establece un controlador **abort** de `raise(SIGABRT)`señal no predeterminado, anule las llamadas . Use la función [signal](signal.md) para asociar una función de controlador de señales de anulación a la señal `SIGABRT`. Puede realizar acciones personalizadas (por ejemplo, limpiar recursos o registrar información) y finalizar la aplicación con su propio código de error en la función de controlador. Si no se define ningún controlador de `SIGABRT` señal personalizado, **abortar** no aumenta la señal.

De forma predeterminada, en compilaciones que no son de depuración de aplicaciones de escritorio o de consola, **abortar** y, a continuación, invocar el mecanismo de servicio de informes de errores de Windows (anteriormente conocido como Dr. Watson) para notificar errores a Microsoft. Este comportamiento se puede habilitar o deshabilitar mediante una llamada a `_set_abort_behavior` y al establecer o enmascarar la marca `_CALL_REPORTFAULT`. Cuando se establece la marca, Windows muestra un cuadro de mensaje cuyo texto es similar a "El programa dejó de funcionar correctamente por un problema". El usuario puede invocar un depurador con un botón **Depurar** o elegir el botón **Cerrar programa** para finalizar la aplicación con un código de error definido por el sistema operativo.

Si no se invoca el controlador de informes de errores de Windows, **anule** las llamadas [_exit](exit-exit-exit.md) para finalizar el proceso con el código de salida 3 y devuelve el control al proceso primario o al sistema operativo. `_exit` no vacía los búferes de secuencias ni realiza el procesamiento de `atexit`/`_onexit`.

Para obtener más información sobre la depuración de CRT, consulte [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).

**Fin de Específicos de Microsoft**

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**Aborta**|\<process.h> o \<stdlib.h>|

## <a name="example"></a>Ejemplo

El siguiente programa intenta abrir un archivo y se anula si se produce un error en el intento.

```C
// crt_abort.c
// compile with: /TC
// This program demonstrates the use of
// the abort function by attempting to open a file
// and aborts if the attempt fails.

#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    FILE    *stream = NULL;
    errno_t err = 0;

    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );
    if ((err != 0) || (stream == NULL))
    {
        perror( "File could not be opened" );
        abort();
    }
    else
    {
        fclose( stream );
    }
}
```

```Output
File could not be opened: No such file or directory
```

## <a name="see-also"></a>Consulte también

[Usar abort](../../cpp/using-abort.md)<br/>
[abort (Función)](../../c-language/abort-function-c.md)<br/>
[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec funciones](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[raise](raise.md)<br/>
[Señal](signal.md)<br/>
[_spawn, funciones _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)
