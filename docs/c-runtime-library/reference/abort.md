---
title: abort | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02e8c81ef539dc2f078a3b120ca673a0ef612779
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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

`abort` no devuelve el control al proceso de llamada. De forma predeterminada, busca un controlador de señales de anulación y genera `SIGABRT` si se ha establecido uno. Luego, `abort` finaliza el proceso actual y devuelve un código de salida al proceso primario.

## <a name="remarks"></a>Comentarios

**Específicos de Microsoft**

De forma predeterminada, cuando se compila una aplicación con la biblioteca de depuración en tiempo de ejecución, la rutina `abort` muestra un mensaje de error antes de generar `SIGABRT`. En el caso de aplicaciones de consola que se ejecuten en modo de consola, el mensaje se envía a `STDERR`. Las aplicaciones de escritorio de Windows y las aplicaciones de consola que se ejecutan en modo de ventana muestran el mensaje en un cuadro de mensaje. Para suprimir el mensaje, use [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md) para borrar la marca `_WRITE_ABORT_MSG`. El mensaje que aparece depende de la versión del entorno en tiempo de ejecución que se use. Para las aplicaciones compiladas con las versiones más recientes de Visual C++, el mensaje es similar a esto:

> Se ha llamado R6010 - abort()

En versiones anteriores de la biblioteca en tiempo de ejecución de C, se muestra este mensaje:

> Esta aplicación solicitó la finalización del tiempo de ejecución de modo no habitual. Póngase en contacto con el equipo de asistencia técnica de la aplicación para obtener más información.

Cuando el programa se compila en modo de depuración, el cuadro de mensaje muestra opciones para **Anular**, **Reintentar** u **Omitir**. Si el usuario elige **Anular**, el programa finaliza inmediatamente y devuelve un código de salida de 3. Si el usuario elige **Reintentar**, se invoca a un depurador para la depuración Just-In-Time, si está disponible. Si el usuario elige **Omitir**, `abort` continúa el procesamiento normal.

En las versiones comerciales y de depuración, `abort` comprueba si se establece un controlador de señales de anulación. Si se establece un controlador de señales no predeterminado, `abort` llama a `raise(SIGABRT)`. Use la función [signal](../../c-runtime-library/reference/signal.md) para asociar una función de controlador de señales de anulación a la señal `SIGABRT`. Puede realizar acciones personalizadas (por ejemplo, limpiar recursos o registrar información) y finalizar la aplicación con su propio código de error en la función de controlador. Si no se define ningún controlador de señales personalizado, `abort` no genera la señal `SIGABRT`.

De forma predeterminada, en las compilaciones de depuración no de las aplicaciones de escritorio o de consola, `abort` , a continuación, se invoca el mecanismo de servicio de informes de errores de Windows (anteriormente conocido como recuperación ante desastres. Watson) para notificar errores a Microsoft. Este comportamiento se puede habilitar o deshabilitar mediante una llamada a `_set_abort_behavior` y al establecer o enmascarar la marca `_CALL_REPORTFAULT`. Cuando se establece la marca, Windows muestra un cuadro de mensaje cuyo texto es similar a "El programa dejó de funcionar correctamente por un problema". El usuario puede invocar un depurador con un botón **Depurar** o elegir el botón **Cerrar programa** para finalizar la aplicación con un código de error definido por el sistema operativo.

Si no se invoca al controlador de informe de errores de Windows, `abort` llama a [_exit](../../c-runtime-library/reference/exit-exit-exit.md) para finalizar el proceso con el código de salida 3 y devuelve el control al proceso primario o al sistema operativo. `_exit` no vacía los búferes de secuencias ni realiza el procesamiento de `atexit`/`_onexit`.

Para obtener más información sobre la depuración de CRT, consulte [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).

**Fin de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`abort`|\<process.h> o \<stdlib.h>|

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

[Usar abort](../../cpp/using-abort.md)  
[abort (Función)](../../c-language/abort-function-c.md)  
[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)  
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)  
[exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)  
[raise](../../c-runtime-library/reference/raise.md)  
[signal](../../c-runtime-library/reference/signal.md)  
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)  
[_DEBUG](../../c-runtime-library/debug.md)  
[_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)  

