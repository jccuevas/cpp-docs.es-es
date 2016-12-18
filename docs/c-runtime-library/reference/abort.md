---
title: "abort | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "abort"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "Abort"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "abort (función)"
  - "anular proceso actual"
  - "procesos, anular"
ms.assetid: a797783b-40ed-4bdb-a2cd-14ffede39e8a
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# abort
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Anula el proceso actual y devuelve un código de error.  
  
> [!NOTE]
>  No use este método para cerrar una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], salvo en escenarios de prueba o depuración.  Las formas de cerrar mediante programación o con la interfaz de usuario una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] no se permiten según los [Requisitos de certificación para una aplicación de Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889).  Para obtener más información, vea [Ciclo de vida de la aplicación \(aplicaciones de la Tienda Windows\)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## Sintaxis  
  
```  
void abort( void );  
```  
  
## Valor devuelto  
 `abort` no devuelve ningún control al proceso de llamada.  De forma predeterminada, comprueba si hay un controlador de la señal de anulación y produce una `SIGABRT` si hay uno establecido.  Después de `abort` finaliza el proceso actual y devuelve un código de salida al proceso primario.  
  
## Comentarios  
 **Específicos de Microsoft**  
  
 De forma predeterminada, cuando se compila una aplicación con la biblioteca en tiempo de ejecución de depuración, la rutina `abort` muestra un mensaje de error antes de que se genere `SIGABRT` .  En las aplicaciones de consola que se ejecutan en modo de consola, el mensaje se envía a `STDERR`.  Las aplicaciones de escritorio Windows y aplicaciones de consola que se ejecutan en modo de ventanas muestran el mensaje en un cuadro de mensaje.  Para suprimir el mensaje, utilice [\_set\_abort\_behavior](../../c-runtime-library/reference/set-abort-behavior.md) para borrar la marca `_WRITE_ABORT_MSG` .  El mensaje mostrado depende de la versión del entorno de runtime utilizado.  En las aplicaciones compiladas con la versión más reciente de Visual C\+\+, el mensaje tiene la apariencia siguiente:  
  
 `R6010`  
  
 `- abort() has been called`  
  
 En versiones anteriores de la biblioteca en tiempo de ejecución de C, se mostró este mensaje:  
  
 "`This application has requested the Runtime to terminate it in an unusual way. Please contact the application's support team for more information.`"  
  
 Cuando el programa se compila en modo de depuración, el cuadro de mensaje muestra las opciones **Anular**, **Reintentar** u **Omitir**.  Si el usuario elige **Anular**, el programa finaliza inmediatamente y devuelve un código de salida 3.  Si el usuario elige **Reintentar**, se invoca un depurador para la depuración Just\-In\-Time, si está disponible.  Si el usuario elige **Omitir**, `abort` continúa el procesamiento normal.  
  
 En ambos casos, en compilaciones comerciales y de depuración, `abort` comprueba si se establecen un controlador de la señal de anulación.  Si se establece un controlador de señal no predeterminado, `abort` llama a `raise(SIGABRT)`.  Utilice la función [signal](../../c-runtime-library/reference/signal.md) para asociar una función controladora de la señal de anulación con la señal `SIGABRT`.  Puede realizar acciones personalizadas, por ejemplo, limpiar recursos o registrar información, y finalizar la aplicación con su propio código de error en la función controladora.  Si no se define ningún controlador de señal personalizado, `abort` no genera la señal `SIGABRT`.  
  
 De forma predeterminada, en las compilaciones que no son de depuración de aplicaciones de escritorio o de consola, `abort` invoca entonces el mecanismo de notificación de errores de Windows \(Dr.  Watson\) para informar sobre errores a Microsoft.  Este comportamiento se puede habilitar o deshabilitar si llama a `_set_abort_behavior` y establece o enmascara la marca `_CALL_REPORTFAULT`.  Cuando se establece la marca, Windows muestra un cuadro de mensaje que tiene un texto similar a “Un problema hizo que el programa dejara de funcionar correctamente”. El usuario puede elegir para invocar un depurador con un botón **Depurar** o elegir el botón **Cerrar programa** para finalizar la aplicación con un código de error definido por el sistema operativo.  
  
 Si no se invoca el controlador Informe de errores de Windows, `abort` llama a [\_exit](../../c-runtime-library/reference/exit-exit-exit.md) para finalizar el proceso con el código de salida 3 y devolverá el control al proceso primario o al sistema operativo.  `_exit` no vacía los búferes de secuencias ni realiza ningún procesamiento `atexit`\/`_onexit` .  
  
 Para obtener más información acerca de la depuración CRT, vea [Técnicas de depuración de CRT](../Topic/CRT%20Debugging%20Techniques.md).  
  
 **Fin de Específicos de Microsoft**  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`abort`|\<process.h\> o \<stdlib.h\>|  
  
## Ejemplo  
 El siguiente programa intenta abrir un archivo y se anula si se produce un error en el intento.  
  
```c  
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
  
  **El archivo no se pudo abrir: no existe el archivo o directorio**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Usar abort](../../cpp/using-abort.md)   
 [abort \(Función\)](../../c-language/abort-function-c.md)   
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [\_exec, \_wexec \(Funciones\)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [raise](../../c-runtime-library/reference/raise.md)   
 [signal](../../c-runtime-library/reference/signal.md)   
 [\_spawn, \_wspawn \(Funciones\)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [\_DEBUG](../../c-runtime-library/debug.md)   
 [\_set\_abort\_behavior](../../c-runtime-library/reference/set-abort-behavior.md)