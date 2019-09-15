---
title: signal
ms.date: 04/12/2018
api_name:
- signal
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 04869412272725108911f13857585e650ad20ab9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948101"
---
# <a name="signal"></a>signal

Determina el control de señales de interrupción.

> [!IMPORTANT]
> No use este método para cerrar una aplicación Microsoft Store, excepto en escenarios de prueba o depuración. No se permiten las formas de cerrar una aplicación de la tienda mediante programación o la interfaz de usuario de acuerdo con las [directivas de Microsoft Store](/legal/windows/agreements/store-policies). Para obtener más información, consulte el ciclo de vida de las [aplicaciones para UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Sintaxis

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Parámetros

*sig*<br/>
Valor de la señal.

*func*<br/>
El segundo parámetro es un puntero a la función que se va a ejecutar. El primer parámetro es un valor de señal y el segundo es un subcódigo que se puede usar cuando el primer parámetro es SIGFPE.

## <a name="return-value"></a>Valor devuelto

**Signal** devuelve el valor anterior de FUNC que está asociado a la señal determinada. Por ejemplo, si el valor anterior de *FUNC* era **SIG_IGN**, el valor devuelto también es **SIG_IGN**. Un valor devuelto de **SIG_ERR** indica un error; en ese caso, **errno** se establece en **EINVAL**.

Vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre los códigos de retorno.

## <a name="remarks"></a>Comentarios

La función **Signal** permite que un proceso elija una de varias maneras de controlar una señal de interrupción desde el sistema operativo. El argumento *SIG* es la interrupción a la que responde la **señal** ; debe ser una de las constantes de manifiesto siguientes, que se definen en la señal. C.

|valor *SIG*|DESCRIPCIÓN|
|-----------------|-----------------|
|**SIGABRT**|Terminación anómala|
|**SIGFPE**|Error de punto flotante|
|**SIGILL**|Instrucción no válida|
|**SIGINT**|Señal de CTRL+C|
|**SIGSEGV**|Acceso no válido a almacenamiento|
|**SIGTERM**|Solicitud de finalización|

Si *SIG* no es ninguno de los valores anteriores, se invoca el controlador de parámetros no válidos, tal y como se define en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **SIG_ERR**.

De forma predeterminada, la **señal** finaliza el programa de llamada con el código de salida 3, independientemente del valor de *SIG*.

> [!NOTE]
> **SIGINT** no es compatible con ninguna aplicación Win32. Cuando se produce una interrupción de CTRL+C, los sistemas operativos de Win32 generan un subproceso nuevo para controlar esa interrupción específicamente. Así se puede hacer que una aplicación de un único subproceso, por ejemplo una de UNIX, se convierta en aplicación multiproceso y provoque un comportamiento inesperado.

El argumento *FUNC* es una dirección de un controlador de señal que se escribe o en una de las constantes predefinidas **SIG_DFL** o **SIG_IGN**, que también se definen en la señal. C. Si *FUNC* es una función, se instala como controlador de señal para la señal determinada. El prototipo del controlador de señal requiere un argumento formal, *SIG*, de tipo **int**. El sistema operativo proporciona el argumento real a través de *SIG* cuando se produce una interrupción. el argumento es la señal que generó la interrupción. Por consiguiente, puede usar las seis constantes de manifiesto de la tabla anterior en el controlador de señal para determinar qué interrupción se produjo y tomar las medidas adecuadas. Por ejemplo, puede llamar a **Signal** dos veces para asignar el mismo controlador a dos señales diferentes y, a continuación, probar el argumento *SIG* en el controlador para realizar distintas acciones en función de la señal recibida.

Si está probando las excepciones de punto flotante (**SIGFPE**), *FUNC* apunta a una función que toma un segundo argumento opcional que es una de varias constantes de manifiesto, definidas en float. H, con el formato **FPE_xxx**. Cuando se produce una señal **SIGFPE** , puede probar el valor del segundo argumento para determinar el tipo de excepción de punto flotante y, a continuación, tomar las medidas adecuadas. Este argumento y sus valores posibles son extensiones de Microsoft.

En el caso de las excepciones de punto flotante, el valor de *FUNC* no se restablece cuando se recibe la señal. Para recuperarse de excepciones de punto flotante, utilice cláusulas Try o Except para rodear las operaciones de punto flotante. También se puede recuperar usando [setjmp](setjmp.md) con [longjmp](longjmp.md). En cualquier caso, el proceso de llamada reanuda la ejecución y deja el estado de punto flotante del proceso sin definir.

Si vuelve el controlador de señal, el proceso de llamada reanuda la ejecución inmediatamente después del punto en el que recibió la señal de interrupción. Es así independientemente de la clase de señal o del modo de funcionamiento.

Antes de que se ejecute la función especificada, el valor de *FUNC* se establece en **SIG_DFL**. La siguiente señal de interrupción se trata como se describe en **SIG_DFL**, a menos que una llamada intermedia a **Signal** especifique lo contrario. Puede usar esta característica para restablecer señalas en la función a la que se llama.

Dado que se suele llamar a las rutinas de controlador de señal de forma asincrónica cuando se produce una interrupción, la función del controlador de señal puede hacerse con el control cuando una operación de tiempo de ejecución no está completa y está en un estado desconocido. En la lista siguiente se resumen las restricciones que determinan qué funciones se pueden usar en la rutina del controlador de señal.

- No emita bajo nivel ni STDIO. Las rutinas de e/s de H (por ejemplo, **printf** o **fread**).

- No llame a rutinas del montón ni a ninguna rutina que use las rutinas del montón (por ejemplo, **malloc**, **_strdup**o **_putenv**). Vea [malloc](malloc.md) para obtener más información.

- No use ninguna función que genere una llamada del sistema (por ejemplo, **_getcwd** o **Time**).

- No utilice **longjmp** a menos que la interrupción se deba a una excepción de punto flotante (es decir, que *SIG* sea **SIGFPE**). En este caso, reinicialice primero el paquete de punto flotante mediante una llamada a **_fpreset**.

- No use ninguna rutina superpuesta.

Un programa debe contener código de punto flotante si se va a capturar la excepción **SIGFPE** mediante la función. Si el programa no tiene código de punto flotante y requiere el código de control de señal de la biblioteca en tiempo de ejecución, simplemente declare un doble volátil e inicialícelo en cero:

```C
volatile double d = 0.0f;
```

Las señales **SIGILL** y **SIGTERM** no se generan en Windows. Se incluyen para razones de compatibilidad con ANSI. Por lo tanto, puede establecer controladores de señal para estas señales mediante **Signal**, y también puede generar estas señales explícitamente llamando a [raise](raise.md).

La configuración de la señal no se conserva en los procesos generados que se crean mediante llamadas a las funciones [_exec](../../c-runtime-library/exec-wexec-functions.md) o [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) . Las configuraciones de las señales se restablecen a los valores predeterminados en el proceso nuevo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**signal**|\<signal.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar **Signal** para agregar algún comportamiento personalizado a la señal **SIGABRT** . Para obtener más información sobre el comportamiento de anulación, vea [_set_abort_behavior](set-abort-behavior.md).

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>
#include <tchar.h>

void SignalHandler(int signal)
{
    if (signal == SIGABRT) {
        // abort signal handler code
    } else {
        // ...
    }
}

int main()
{
    typedef void (*SignalHandlerPointer)(int);

    SignalHandlerPointer previousHandler;
    previousHandler = signal(SIGABRT, SignalHandler);

    abort();
}
```

```Output
This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
