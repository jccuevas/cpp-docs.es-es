---
title: "exit, _Exit, _exit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_exit"
  - "exit"
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
  - "Exit"
  - "_exit"
  - "process/exit"
  - "process/_Exit"
  - "stdlib/exit"
  - "stdlib/_Exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exit (función)"
  - "_exit (función)"
  - "procesos, terminar"
  - "llamadas a funciones, terminar"
  - "finalización del proceso, llamar"
ms.assetid: b1501fa6-27c2-478c-9e93-cc4fd802a01f
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# exit, _Exit, _exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Finaliza el proceso de llamada. La función `exit` lo finaliza después de la limpieza; `_exit` y `_Exit` lo finalizan inmediatamente.  
  
> [!NOTE]
>  No utilice este método para cerrar una aplicación de la Plataforma universal de Windows \(UWP\) o una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], excepto en escenarios de pruebas o depuración. Las formas de cerrar una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] mediante programación o la interfaz de usuario no se permiten. Para más información sobre las aplicaciones de Windows 8 y 8.1, consulte [Ciclo de vida de la aplicación](http://go.microsoft.com/fwlink/?LinkId=262853). Para más información sobre las aplicaciones de Windows 10, consulte [Guías de procedimientos para aplicaciones de Windows 10](http://go.microsoft.com/fwlink/p/?linkid=619133).  
  
## Sintaxis  
  
```  
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
  
#### Parámetros  
 `status`  
 Código de estado de salida.  
  
## Comentarios  
 Las funciones `exit`, `_Exit` y `_exit` finalizan el proceso que realiza la llamada. La función `exit` llama a destructores para los objetos locales para el subproceso y, después, llama \(en orden LIFO, donde el último en entrar es primero en salir\) a las funciones registradas por `atexit` y `_onexit` para, a continuación, vaciar todos los búferes de archivo antes de finalizar el proceso. Las funciones `_Exit` y `_exit` finalizan el proceso sin destruir objetos locales para el subproceso ni procesar funciones `atexit` o `_onexit` y sin vaciar los búferes de secuencia.  
  
 Aunque las llamadas a `exit`, `_Exit` y `_exit` no devuelven ningún valor, el byte de orden inferior de `status` se pone a disposición del proceso de llamada en espera o de entorno de host, si existe uno de ellos, una vez que ha finalizado el proceso. Normalmente, el autor de la llamada establece el valor de `status` en 0 para indicar una salida normal, o en otro valor para indicar un error. El valor de `status` está disponible para el comando de proceso por lotes `ERRORLEVEL` del sistema operativo y se representa mediante una de dos constantes: `EXIT_SUCCESS`, que representa un valor de 0, o `EXIT_FAILURE`, que representa un valor de 1.  
  
 Las funciones `exit`, `_Exit`, `_exit`, `quick_exit`, `_cexit` y `_c_exit` se comportan como sigue.  
  
|Función|Descripción|  
|-------------|-----------------|  
|`exit`|Realiza procedimientos completos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|  
|`_Exit`|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|  
|`_exit`|Realiza procedimientos mínimos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|  
|`quick_exit`|Realiza procedimientos rápidos de finalización de la biblioteca de C, finaliza el proceso y proporciona el código de estado facilitado al entorno de host.|  
|`_cexit`|Realiza procedimientos completos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|  
|`_c_exit`|Realiza procedimientos mínimos de finalización de la biblioteca de C y vuelve al llamador. No finaliza el proceso.|  
  
 Cuando se llama a la función `exit`, `_Exit` o `_exit`, no se llama a los destructores de ningún objeto temporal o automático que exista en el momento de la llamada. Un objeto automático se define en una función en la que el objeto no se declara como estático. Un objeto temporal es un objeto creado por el compilador. Para destruir un objeto automático antes de llamar a `exit`, `_Exit` o `_exit`, llame explícitamente al destructor del objeto, como se indica a continuación:  
  
```  
myObject.myClass::~myClass();  
```  
  
 No use `DLL_PROCESS_ATTACH` para llamar a `exit` desde `DllMain`. Si desea cerrar la función `DLLMain`, devuelva `FALSE` desde `DLL_PROCESS_ATTACH`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`exit`, `_Exit`, `_exit`|\<process.h\> o \<stdlib.h\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_exit.c // This program returns an exit code of 1. The // error code could be tested in a batch file. #include <stdlib.h> int main( void ) { exit( 1 ); }  
```  
  
## Equivalente en .NET Framework  
 [System::Diagnostics::Process::Kill](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_cexit, \_c\_exit](../../c-runtime-library/reference/cexit-c-exit.md)   
 [\_exec, \_wexec \(Funciones\)](../../c-runtime-library/exec-wexec-functions.md)   
 [\_onexit, \_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [quick\_exit](../../c-runtime-library/reference/quick-exit1.md)   
 [\_spawn, \_wspawn \(Funciones\)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, \_wsystem](../../c-runtime-library/reference/system-wsystem.md)