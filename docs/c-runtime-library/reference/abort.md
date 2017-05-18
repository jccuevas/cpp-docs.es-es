---
title: abort | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: a797783b-40ed-4bdb-a2cd-14ffede39e8a
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 18a683e6581f979c0383c76a3ada2a8e80316255
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="abort"></a>abort
Anula el proceso actual y devuelve un código de error.  
  
> [!NOTE]
>  No use este método para cerrar una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], salvo en escenarios de prueba o depuración. Las formas de cerrar una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] mediante programación o con la interfaz de usuario no están permitidas según los [Requisitos para la certificación de aplicaciones de Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Para obtener más información, consulte [Ciclo de vida de la aplicación (aplicaciones de la Tienda Windows)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void abort( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 `abort` no devuelve el control al proceso de llamada. De forma predeterminada, busca un controlador de señales de anulación y genera `SIGABRT` si se ha establecido uno. Luego, `abort` finaliza el proceso actual y devuelve un código de salida al proceso primario.  
  
## <a name="remarks"></a>Comentarios  
 **Específicos de Microsoft**  
  
 De forma predeterminada, cuando se compila una aplicación con la biblioteca de depuración en tiempo de ejecución, la rutina `abort` muestra un mensaje de error antes de generar `SIGABRT`. En el caso de aplicaciones de consola que se ejecuten en modo de consola, el mensaje se envía a `STDERR`. Las aplicaciones de escritorio de Windows y las aplicaciones de consola que se ejecutan en modo de ventana muestran el mensaje en un cuadro de mensaje. Para suprimir el mensaje, use [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md) para borrar la marca `_WRITE_ABORT_MSG`. El mensaje que aparece depende de la versión del entorno en tiempo de ejecución que se use. Para las aplicaciones compiladas con la versión más reciente de Visual C++, el mensaje se parece al siguiente:  
  
 `R6010`  
  
 `- abort() has been called`  
  
 En versiones anteriores de la biblioteca en tiempo de ejecución de C, se muestra este mensaje:  
  
 "`This application has requested the Runtime to terminate it in an unusual way. Please contact the application's support team for more information.`"  
  
 Cuando el programa se compila en modo de depuración, el cuadro de mensaje muestra opciones para **Anular**, **Reintentar** u **Omitir**. Si el usuario elige **Anular**, el programa finaliza inmediatamente y devuelve un código de salida de 3. Si el usuario elige **Reintentar**, se invoca a un depurador para la depuración Just-In-Time, si está disponible. Si el usuario elige **Omitir**, `abort` continúa el procesamiento normal.  
  
 En las versiones comerciales y de depuración, `abort` comprueba si se establece un controlador de señales de anulación. Si se establece un controlador de señales no predeterminado, `abort` llama a `raise(SIGABRT)`. Use la función [signal](../../c-runtime-library/reference/signal.md) para asociar una función de controlador de señales de anulación a la señal `SIGABRT`. Puede realizar acciones personalizadas (por ejemplo, limpiar recursos o registrar información) y finalizar la aplicación con su propio código de error en la función de controlador. Si no se define ningún controlador de señales personalizado, `abort` no genera la señal `SIGABRT`.  
  
 De forma predeterminada, en versiones que no sean de depuración de aplicaciones de escritorio o de consola, `abort` invoca después al mecanismo de informe de errores de Windows (Dr. Watson) para notificar errores a Microsoft. Este comportamiento se puede habilitar o deshabilitar mediante una llamada a `_set_abort_behavior` y al establecer o enmascarar la marca `_CALL_REPORTFAULT`. Cuando se establece la marca, Windows muestra un cuadro de mensaje cuyo texto es similar a "El programa dejó de funcionar correctamente por un problema". El usuario puede invocar un depurador con un botón **Depurar** o elegir el botón **Cerrar programa** para finalizar la aplicación con un código de error definido por el sistema operativo.  
  
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
 [_exec, _wexec (Funciones)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [raise](../../c-runtime-library/reference/raise.md)   
 [signal](../../c-runtime-library/reference/signal.md)   
 [_spawn, _wspawn (Funciones)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [_DEBUG](../../c-runtime-library/debug.md)   
 [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)
