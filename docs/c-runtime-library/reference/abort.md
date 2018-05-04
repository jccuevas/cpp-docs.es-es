---
title: abort | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- abort
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
- Abort
dev_langs:
- C++
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 943faab6b13f3d07b2ca19d78c555973149aa4b0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="abort"></a>anular

Anula el proceso actual y devuelve un código de error.

> [!NOTE]
> No utilice este método para cerrar una aplicación de Microsoft Store o una aplicación de plataforma Universal de Windows (UWP), excepto en pruebas o en escenarios de depuración. No se permiten formas mediante programación o la interfaz de usuario para cerrar una aplicación de tienda según la [las directivas de Microsoft Store](/legal/windows/agreements/store-policies). Para obtener más información, consulte [ciclo de vida de aplicación UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Sintaxis

```c
void abort( void );
```

## <a name="return-value"></a>Valor devuelto

**anular** no devuelve el control al proceso de llamada. De forma predeterminada, busca un controlador de señal de anulación y genera **SIGABRT** si se ha establecido uno. A continuación, **anular** finaliza el proceso actual y devuelve un código de salida para el proceso primario.

## <a name="remarks"></a>Comentarios

**Específicos de Microsoft**

De forma predeterminada, cuando se compila una aplicación con la biblioteca en tiempo de ejecución de depuración, el **anular** rutina muestra un mensaje de error antes de **SIGABRT** se genera. Para aplicaciones de consola que se ejecutan en modo de consola, el mensaje se envía a **STDERR**. Las aplicaciones de escritorio de Windows y las aplicaciones de consola que se ejecutan en modo de ventana muestran el mensaje en un cuadro de mensaje. Para suprimir el mensaje, utilice [_set_abort_behavior](set-abort-behavior.md) para borrar la **_WRITE_ABORT_MSG** marca. El mensaje que aparece depende de la versión del entorno en tiempo de ejecución que se use. Para las aplicaciones compiladas con las versiones más recientes de Visual C++, el mensaje es similar a esto:

> Se ha llamado R6010 - abort()

En versiones anteriores de la biblioteca en tiempo de ejecución de C, se muestra este mensaje:

> Esta aplicación solicitó la finalización del tiempo de ejecución de modo no habitual. Póngase en contacto con el equipo de asistencia técnica de la aplicación para obtener más información.

Cuando el programa se compila en modo de depuración, el cuadro de mensaje muestra opciones para **Anular**, **Reintentar** u **Omitir**. Si el usuario elige **Anular**, el programa finaliza inmediatamente y devuelve un código de salida de 3. Si el usuario elige **Reintentar**, se invoca a un depurador para la depuración Just-In-Time, si está disponible. Si el usuario elige **omitir**, **anular** continúa el procesamiento normal.

En las compilaciones comerciales y de depuración, **anular** , a continuación, comprueba si se configura un controlador de señal de anulación. Si se establece un controlador de señal no predeterminado, **anular** llamadas `raise(SIGABRT)`. Use la [señal](signal.md) función para asociar una función del controlador de señal de interrupción con el **SIGABRT** señal. Puede realizar acciones personalizadas (por ejemplo, limpiar recursos o registrar información) y finalizar la aplicación con su propio código de error en la función de controlador. Si no se ha definido ningún controlador de señal personalizado, **anular** no provoca la **SIGABRT** señal.

De forma predeterminada, en las compilaciones de depuración no de las aplicaciones de escritorio o de consola, **anular** , a continuación, se invoca el mecanismo de servicio de informes de errores de Windows (anteriormente conocido como recuperación ante desastres. Watson) para notificar errores a Microsoft. Este comportamiento se puede habilitar o deshabilitar mediante una llamada a **_set_abort_behavior** y establecer o enmascarando la **_CALL_REPORTFAULT** marca. Cuando se establece la marca, Windows muestra un cuadro de mensaje cuyo texto es similar a "El programa dejó de funcionar correctamente por un problema". El usuario puede invocar un depurador con un botón **Depurar** o elegir el botón **Cerrar programa** para finalizar la aplicación con un código de error definido por el sistema operativo.

Si los informes de controlador de errores de Windows no se invocan, a continuación, **anular** llamadas [_exit](exit-exit-exit.md) para finalizar el proceso con salida código 3 y devuelve el control para el proceso primario o el sistema operativo. **_Exit** no vaciar los búferes de secuencia o realizar **atexit**/**_onexit** de procesamiento.

Para más información sobre la depuración, vea [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).

**Fin de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**abort**|\<process.h> o \<stdlib.h>|

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

## <a name="see-also"></a>Vea también

[Usar abort](../../cpp/using-abort.md)<br/>
[abort (Función)](../../c-language/abort-function-c.md)<br/>
[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)<br/>
