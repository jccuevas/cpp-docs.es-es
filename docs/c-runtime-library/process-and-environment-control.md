---
title: "Control de proceso y de entorno | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.programs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rutinas de control de entorno"
  - "proceso primario"
  - "rutinas de control de proceso"
  - "procesos, tareas administrativas"
  - "procesos, iniciar"
  - "procesos, detener"
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Control de proceso y de entorno
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice las rutinas del proceso CONTROL para iniciar, detener, y administrar procesos dentro de un programa.  Utilice las rutinas de la intermediate language CONTROL para obtener y la información de cambio sobre el entorno del sistema operativo.  
  
### Funciones de procesos y de control ambiental  
  
|Rutina|Utilice|Equivalente de .NET Framework|  
|------------|-------------|-----------------------------------|  
|[anulación](../c-runtime-library/reference/abort.md)|El proceso de anulación sin vaciar los búferes o las funciones de llamada registrado por `atexit` y `_onexit`|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|Prueba del error lógico|[\<caps:sentence id\="tgt14" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|macros de[\_ASSERT; \_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Similar a `assert`, pero sólo está disponible en las versiones de depuración de las bibliotecas en tiempo de ejecución|[\<caps:sentence id\="tgt17" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[atexit](../c-runtime-library/reference/atexit.md)|Rutinas de programación para la ejecución en la finalización del programa|[\<caps:sentence id\="tgt20" sentenceid\="db022fa9aa2a12937c3610e3eb32e80f" class\="tgtSentence"\>System::Diagnostics::Process::Exited\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)|  
|[\_beginthread, \_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|Cree un nuevo subproceso de un proceso del sistema operativo Windows|[\<caps:sentence id\="tgt23" sentenceid\="221e38ecc6535bce91af4e1a19f464d1" class\="tgtSentence"\>System::Threading::Thread::Start\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.threading.thread.start.aspx)|  
|[\_cexit](../c-runtime-library/reference/cexit-c-exit.md)|Siga los procedimientos de finalización de `exit` \(como vaciar los búferes\), se devuelve el control al programa de llamada sin terminar proceso|[\<caps:sentence id\="tgt26" sentenceid\="46302f19d05c09c5875a795cb64800f9" class\="tgtSentence"\>System::Diagnostics::Process::CloseMainWindow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)|  
|[\_c\_exit](../c-runtime-library/reference/cexit-c-exit.md)|Siga los procedimientos de finalización de `_exit` , después devuelve el control al programa de llamada sin terminar proceso|[\<caps:sentence id\="tgt29" sentenceid\="46302f19d05c09c5875a795cb64800f9" class\="tgtSentence"\>System::Diagnostics::Process::CloseMainWindow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)|  
|[\_cwait](../c-runtime-library/reference/cwait.md)|Espere hasta que otro proceso finalice|[\<caps:sentence id\="tgt32" sentenceid\="d9c88c429eaacaa9f37d91d29bc6504e" class\="tgtSentence"\>System::Diagnostics::Process::WaitForExit\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.waitforexit.aspx)|  
|[\_endthread, \_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|Finaliza un subproceso del sistema operativo Windows|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_execl, \_wexecl](../c-runtime-library/reference/execl-wexecl.md)|Ejecuta el nuevo proceso con la lista de argumentos|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execle, \_wexecle](../c-runtime-library/reference/execle-wexecle.md)|Ejecuta el nuevo proceso con la lista de argumentos y el entorno determinado|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execlp, \_wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|Ejecuta el nuevo proceso utilizando la variable y la lista de argumentos de `PATH`|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execlpe, \_wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|Ejecuta el nuevo proceso utilizando la variable de `PATH` , según el entorno, y la lista de argumentos|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execv, \_wexecv](../c-runtime-library/reference/execv-wexecv.md)|Ejecuta el nuevo proceso con matriz de argumentos|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execve, \_wexecve](../c-runtime-library/reference/execve-wexecve.md)|Ejecuta el nuevo proceso con la matriz de argumentos y el entorno determinado|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execvp, \_wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|Ejecuta el nuevo proceso utilizando la variable de `PATH` y la matriz de argumentos|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execvpe, \_wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|Ejecuta el nuevo proceso utilizando la variable de `PATH` , según el entorno, y la matriz de argumentos|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[exit](../c-runtime-library/reference/exit-exit-exit.md)|Llame a las funciones registradas por `atexit` y `_onexit`, borre todos los búferes, cierre todos los archivos abiertos, y finalice el proceso|[\<caps:sentence id\="tgt64" sentenceid\="811a70e90f150f212690505b37a46c0f" class\="tgtSentence"\>System::Diagnostics::Process::Kill\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)|  
|[\_exit](../c-runtime-library/reference/exit-exit-exit.md)|Finalice el proceso inmediatamente sin llamar a `atexit` o `_onexit` o vaciar los búferes|[\<caps:sentence id\="tgt67" sentenceid\="811a70e90f150f212690505b37a46c0f" class\="tgtSentence"\>System::Diagnostics::Process::Kill\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)|  
|[getenv, \_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md), [getenv\_s, \_wgetenv\_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|Obtenga el valor de la variable de entorno|[\<caps:sentence id\="tgt70" sentenceid\="795988b9277d74ea3b722ecd42dcb29d" class\="tgtSentence"\>System::Environment::GetEnvironmentVariable\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)|  
|[\_getpid](../c-runtime-library/reference/getpid.md)|Obtiene el número de identificador de proceso|[\<caps:sentence id\="tgt73" sentenceid\="745b82c461dc74b15540e9622f7cd7bd" class\="tgtSentence"\>System::Diagnostics::Process::Id\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)|  
|[longjmp](../c-runtime-library/reference/longjmp.md)|Restaurar el entorno de la pila; utilícelo para ejecutar `goto`local|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|Rutinas de programación para la ejecución en la finalización del programa; utiliza la compatibilidad con la versión 7.0 de Microsoft C\/C\+\+ y anterior|[\<caps:sentence id\="tgt81" sentenceid\="db022fa9aa2a12937c3610e3eb32e80f" class\="tgtSentence"\>System::Diagnostics::Process::Exited\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)|  
|[\_pclose](../c-runtime-library/reference/pclose.md)|Al nuevo procesador de comandos y cierre secuencia de canalización asociada|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[perror, \_wperror](../c-runtime-library/reference/perror-wperror.md)|Mensaje de error de impresión|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_pipe](../c-runtime-library/reference/pipe.md)|Cree la canalización para leer y escribir|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_popen, \_wpopen](../c-runtime-library/reference/popen-wpopen.md)|Cree la canalización y ejecute el comando|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_putenv, \_wputenv](../c-runtime-library/reference/putenv-wputenv.md), [\_putenv\_s, \_wputenv\_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|Agregue o cambie el valor de la variable de entorno|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[raise](../c-runtime-library/reference/raise.md)|Envía la señal al proceso de llamada|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[setjmp](../c-runtime-library/reference/setjmp.md)|Guarde el entorno de la pila; uso de ejecutar `goto`no local|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[señal](../c-runtime-library/reference/signal.md)|Signo de la interrupción de identificador|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_spawnl, \_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|Crear y ejecutar el nuevo proceso con la lista de argumentos especificada|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnle, \_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|Crear y ejecutar el nuevo proceso con la lista de argumentos y el entorno especificados|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnlp, \_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|Crear y ejecutar el nuevo proceso utilizando la variable de `PATH` y la lista de argumentos especificada|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnlpe, \_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|Crear y ejecutar el nuevo proceso utilizando la variable de `PATH` , el entorno especificado, y la lista de argumentos|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnv, \_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|Crear y ejecutar el nuevo proceso con la matriz especificado de argumento|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnve, \_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|Crear y ejecutar el nuevo proceso con la matriz especificado del entorno y argumentos|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnvp, \_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|Crear y ejecutar el nuevo proceso utilizando la variable de `PATH` y la matriz especificado de argumento|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnvpe, \_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|Crear y ejecutar el nuevo proceso utilizando la variable de `PATH` , el entorno especificado, y la matriz de argumentos|[Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx), [Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[el sistema, \_wsystem](../c-runtime-library/reference/system-wsystem.md)|Ejecute el comando del sistema operativo|[Clase de System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx), [Clase de System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)|  
  
 En el sistema operativo Windows, el proceso generado es equivalente al proceso que generar.  Cualquier proceso puede utilizar `_cwait` para esperar cualquier otro proceso para el que se conoce el identificador de proceso.  
  
 La diferencia entre `_exec` y las familias de `_spawn` es que la función de `_spawn` puede devolver el control del nuevo proceso al proceso de llamada.  En una función de `_spawn` , el proceso de llamada y el nuevo proceso están presentes en memoria a menos que se especifique `_P_OVERLAY` .  En una función de `_exec` , el nuevo proceso se superpone al proceso de llamada, por lo que el control no puede volver al proceso de llamada a menos que se produzca un error en el intento de iniciar la ejecución del nuevo proceso.  
  
 Las diferencias entre las funciones de la familia de `_exec` , así como entre las de la familia de `_spawn` , se utiliza el método para buscar el archivo que se ejecutará como el nuevo proceso, la forma en que los argumentos se pasan al nuevo proceso, y el método de establecer el entorno, como se muestra en la tabla siguiente.  Utilice una función que pase una lista de argumentos cuando el número de argumentos es constante o se conoce en tiempo de compilación.  Utilice una función que pase un puntero a una matriz que contiene los argumentos cuando el número de argumentos debe determinar en tiempo de ejecución.  La información en la tabla siguiente también se aplica a sus homólogos de caracteres anchos de `_spawn` y `_exec` funciona.  
  
### familias de la función de \_spawn y de \_exec  
  
|Funciones|Variable PATH de uso para localizar el archivo|Convención para pasar argumentos|Configuración de entorno|  
|---------------|----------------------------------------------------|--------------------------------------|------------------------------|  
|`_execl, _spawnl`|No|Lista|Heredado de proceso de llamada|  
|`_execle, _spawnle`|No|Lista|Puntero a la tabla de entorno para el nuevo proceso pasado como por último argumento|  
|`_execlp, _spawnlp`|Sí|Lista|Heredado de proceso de llamada|  
|`_execlpe, _spawnlpe`|Sí|Lista|Puntero a la tabla de entorno para el nuevo proceso pasado como por último argumento|  
|`_execv, _spawnv`|No|Matriz|Heredado de proceso de llamada|  
|`_execve, _spawnve`|No|Matriz|Puntero a la tabla de entorno para el nuevo proceso pasado como por último argumento|  
|`_execvp, _spawnvp`|Sí|Matriz|Heredado de proceso de llamada|  
|`_execvpe, _spawnvpe`|Sí|Matriz|Puntero a la tabla de entorno para el nuevo proceso pasado como por último argumento|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)