---
title: signal | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- signal
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
- signal
dev_langs:
- C++
helpviewer_keywords:
- signal function
ms.assetid: 094118de-d789-4063-b4f4-cffcc80bf29d
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: b124479c62a62ef7795498b6c4a96191e2ecb6e4
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="signal"></a>signal
Determina el control de señales de interrupción.  
  
> [!IMPORTANT]
>  No use este método para cerrar una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], salvo en escenarios de prueba o depuración. Las formas de cerrar mediante programación o con la interfaz de usuario una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] no se permiten según la Sección 3.6 de los [Requisitos de certificación para una aplicación de Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Para obtener más información, vea [Ciclo de vida de la aplicación (aplicaciones de la Tienda Windows)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void (__cdecl *signal(  
   int sig,   
   void (__cdecl *func ) (int [, int ] )))   
   (int);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `sig`  
 Valor de la señal.  
  
 `func`  
 Función que se va a ejecutar. El primer parámetro es un valor de señal y el segundo es un subcódigo que se puede usar cuando el primer parámetro es SIGFPE.  
  
## <a name="return-value"></a>Valor devuelto  
 `signal` devuelve el valor anterior de `func` asociado a la señal determinada. Por ejemplo, si el valor anterior de `func` era `SIG_IGN`, el valor devuelto también es `SIG_IGN`. Un valor devuelto de `SIG_ERR` indica un error; en ese caso, `errno` se establece en `EINVAL`.  
  
 Vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre los códigos de retorno.  
  
## <a name="remarks"></a>Comentarios  
 La función `signal` permite que un proceso elija una de las maneras de controlar una señal de interrupción del sistema operativo. El argumento de `sig` es la interrupción a la que responde `signal`. Debe ser una de las constantes de manifiesto siguientes, que se definen en SIGNAL.H.  
  
|Valor de `sig`|Descripción|  
|-----------------|-----------------|  
|`SIGABRT`|Terminación anómala|  
|`SIGFPE`|Error de punto flotante|  
|`SIGILL`|Instrucción no válida|  
|`SIGINT`|Señal de CTRL+C|  
|`SIGSEGV`|Acceso no válido a almacenamiento|  
|`SIGTERM`|Solicitud de finalización|  
  
 Si `sig` no es uno de los valores anteriores, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `SIG_ERR`.  
  
 De forma predeterminada, `signal` finaliza el programa de llamada con el código de salida 3, independientemente del valor de `sig`.  
  
> [!NOTE]
>  `SIGINT` no se admite en ninguna aplicación Win32. Cuando se produce una interrupción de CTRL+C, los sistemas operativos de Win32 generan un subproceso nuevo para controlar esa interrupción específicamente. Así se puede hacer que una aplicación de un único subproceso, por ejemplo una de UNIX, se convierta en aplicación multiproceso y provoque un comportamiento inesperado.  
  
 El argumento de `func` es una dirección de un controlador de señal que se escribe, o de una de las constantes predefinidas `SIG_DFL` o `SIG_IGN`, que también se definen en SIGNAL.H. Si `func` es una función, se instala como controlador de señal para la señal determinada. El prototipo del controlador de señal requiere un argumento formal, `sig`, de `int`. El sistema operativo proporciona el argumento real mediante `sig` si se produce una interrupción. El argumento es la señal que generó la interrupción. Por consiguiente, puede usar las seis constantes de manifiesto de la tabla anterior en el controlador de señal para determinar qué interrupción se produjo y tomar las medidas adecuadas. Por ejemplo, puede llamar a `signal` dos veces para asignar el mismo controlador a dos señales distintas, y después probar el argumento de `sig` del controlador para realizar acciones distintas en función de la señal recibida.  
  
 Si desea comprobar las excepciones de punto flotante (`SIGFPE`), `func` señala a una función que toma un segundo argumento opcional que es una de varias constantes de manifiesto, definidas en FLOAT.H, con el formato `FPE_xxx`. Cuando se produce una señal `SIGFPE`, puede probar el valor del segundo argumento para determinar el tipo de excepción de punto flotante y, a continuación, realizar la acción adecuada. Este argumento y sus valores posibles son extensiones de Microsoft.  
  
 En el caso de excepciones de punto flotante, el valor de `func` no se restablece cuando se recibe la señal. Para recuperarse de excepciones de punto flotante, utilice cláusulas Try o Except para rodear las operaciones de punto flotante. También se puede recuperar usando [setjmp](../../c-runtime-library/reference/setjmp.md) con [longjmp](../../c-runtime-library/reference/longjmp.md). En cualquier caso, el proceso de llamada reanuda la ejecución y deja el estado de punto flotante del proceso sin definir.  
  
 Si vuelve el controlador de señal, el proceso de llamada reanuda la ejecución inmediatamente después del punto en el que recibió la señal de interrupción. Es así independientemente de la clase de señal o del modo de funcionamiento.  
  
 Antes de que se ejecute la función especificada, el valor de `func` se establece en `SIG_DFL`. La siguiente señal de interrupción se trata como se describe en `SIG_DFL`, a menos que una llamada intermedia a `signal` especifique otra cosa. Puede usar esta característica para restablecer señalas en la función a la que se llama.  
  
 Dado que se suele llamar a las rutinas de controlador de señal de forma asincrónica cuando se produce una interrupción, la función del controlador de señal puede hacerse con el control cuando una operación de tiempo de ejecución no está completa y está en un estado desconocido. En la lista siguiente se resumen las restricciones que determinan qué funciones se pueden usar en la rutina del controlador de señal.  
  
-   No emita rutinas de E/S de bajo nivel o de STDIO.H (por ejemplo, `printf` o `fread`).  
  
-   No llame a rutinas del montón ni a ninguna rutina que use rutinas del montón (por ejemplo, `malloc`, `_strdup` o `_putenv`). Vea [malloc](../../c-runtime-library/reference/malloc.md) para obtener más información.  
  
-   No use ninguna función que genere una llamada del sistema (por ejemplo, `_getcwd` o `time`).  
  
-   No use `longjmp` a menos que la interrupción sea consecuencia de una excepción de punto flotante (es decir, `sig` es `SIGFPE`). En ese caso, reinicialice primero el paquete de punto flotante mediante una llamada a `_fpreset`.  
  
-   No use ninguna rutina superpuesta.  
  
 Un programa debe contener código de punto flotante para interceptar la excepción de `SIGFPE` mediante la función. Si el programa no tiene código de punto flotante y requiere el código de control de señal de la biblioteca en tiempo de ejecución, simplemente declare un doble volátil e inicialícelo en cero:  
  
`volatile double d = 0.0f;`  
  
 Las señales de `SIGILL` y `SIGTERM` no se generan en Windows. Se incluyen para razones de compatibilidad con ANSI. Por consiguiente, puede establecer controladores de señal para estas señales mediante `signal`. También puede generar estas señales explícitamente llamando a [raise](../../c-runtime-library/reference/raise.md).  
  
 Las configuraciones de las señales no se conservan en los procesos de generación creados mediante llamadas a las funciones `_exec` o `_spawn`. Las configuraciones de las señales se restablecen a los valores predeterminados en el proceso nuevo.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`signal`|\<signal.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar `signal` para agregar comportamiento personalizado a la señal `SIGABRT`. Para obtener más información sobre el comportamiento de anulación, vea [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md).  
  
```cpp  
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
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [_exec, _wexec (Funciones)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_fpreset](../../c-runtime-library/reference/fpreset.md)   
 [_spawn, _wspawn (Funciones)](../../c-runtime-library/spawn-wspawn-functions.md)
