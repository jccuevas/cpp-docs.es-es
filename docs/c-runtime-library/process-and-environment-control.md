---
title: Control de proceso y entorno | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- processes, stopping
- processes, administrative tasks
- parent process
- processes, starting
- environment control routines
- process control routines
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1d2787afe9d2b81e75a2ac0191b0019fb943a00
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="process-and-environment-control"></a>Control de proceso y de entorno

Utilice las rutinas del control de proceso para iniciar, detener, y administrar procesos dentro de un programa. Utilice las rutinas de control de entorno para obtener y cambiar información sobre el entorno del sistema operativo.

## <a name="process-and-environment-control-functions"></a>Funciones del control de proceso y entorno

|Rutina|Usar|
|-------------|---------|
|[abort](../c-runtime-library/reference/abort.md)|Anular el proceso sin vaciar los búferes ni llamar a las funciones registradas por **atexit** y **_onexit**|
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|Prueba de error lógico|
|[_ASSERT, _ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) (Macros)|Similar a **assert**, pero disponible únicamente en las versiones de depuración de las bibliotecas en tiempo de ejecución|
|[atexit](../c-runtime-library/reference/atexit.md)|Programar rutinas para su ejecución al finalizar el programa|
|[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|Crear un nuevo subproceso en un proceso del sistema operativo Windows|
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|Realizar procedimientos de finalización de **exit** (como vaciar búferes) y después devolver el control al programa que realiza la llamada sin finalizar el proceso|
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|Realizar procedimientos de finalización de **_exit** y después devolver el control al programa que realiza la llamada sin finalizar el proceso|
|[_cwait](../c-runtime-library/reference/cwait.md)|Esperar hasta que finalice otro proceso|
|[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|Terminar un subproceso del sistema operativo Windows|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|Ejecutar un proceso nuevo con la lista de argumentos|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|Ejecutar el nuevo proceso con la lista de argumentos y el entorno dado|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|Ejecutar el nuevo proceso mediante la variable **PATH** y la lista de argumentos|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|Ejecutar el nuevo proceso mediante la variable **PATH**, el entorno dado y la lista de argumentos|
|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|Ejecutar un proceso nuevo con la matriz de argumentos|
|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|Ejecutar el nuevo proceso con la matriz de argumentos y el entorno dado|
|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|Ejecutar el nuevo proceso mediante la variable **PATH** y la matriz de argumentos|
|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|Ejecutar el nuevo proceso mediante la variable **PATH**, el entorno dado y la matriz de argumentos|
|[exit](../c-runtime-library/reference/exit-exit-exit.md)|Llamar a las funciones registradas por **atexit** y **_onexit**, vaciar todos los búferes, cerrar todos los archivos abiertos y terminar el proceso|
|[_exit](../c-runtime-library/reference/exit-exit-exit.md)|Terminar el proceso inmediatamente sin llamar a **atexit** o **_onexit** ni vaciar los búferes|
|[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md), [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|Obtener valor de la variable de entorno|
|[_getpid](../c-runtime-library/reference/getpid.md)|Obtener número de identificador del proceso|[System::Diagnostics::Process::Id](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|Restaurar el entorno de pila guardado; usarlo para ejecutar un valor **goto** no local|
|[_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|Programar rutinas para su ejecución al finalizar el programa; usarlas para compatibilidad con Microsoft C/C++ versión 7.0 y anteriores|
|[_pclose](../c-runtime-library/reference/pclose.md)|Esperar al nuevo procesador de comandos y cerrar el flujo en la canalización asociada|
|[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)|Mensaje de error de impresión|
|[_pipe](../c-runtime-library/reference/pipe.md)|Crear una canalización de lectura y escritura|
|[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)|Crear la canalización y ejecutar el comando|
|[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md), [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|Agregar o cambiar el valor de la variable de entorno|
|[raise](../c-runtime-library/reference/raise.md)|Enviar señal al proceso de llamada|
|[setjmp](../c-runtime-library/reference/setjmp.md)|Guardar el entorno de pila; usarlo para ejecutar el valor **goto** no local|
|[signal](../c-runtime-library/reference/signal.md)|Controlar la señal de interrupción|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|Crear y ejecutar un proceso nuevo con la lista de argumentos especificada|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|Crear y ejecutar un proceso nuevo con la lista de argumentos y el entorno especificados|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|Crear y ejecutar un proceso nuevo con la variable **PATH** y la lista de argumentos especificada|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|Crear y ejecutar un proceso nuevo con la variable **PATH**, el entorno especificado y la lista de argumentos|
|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|Crear y ejecutar un proceso nuevo con una matriz de argumentos especificada|
|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|Crear y ejecutar un proceso nuevo con el entorno especificado y la matriz de argumentos|
|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|Crear y ejecutar un proceso nuevo con la variable **PATH** y la matriz de argumentos especificada|
|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|Crear y ejecutar un proceso nuevo con la variable **PATH**, el entorno especificado y la matriz de argumentos|
|[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)|Ejecutar comando del sistema operativo|

 En el sistema operativo Windows, el proceso generado es equivalente al proceso que genera. Cualquier proceso puede usar **_cwait** para esperar a cualquier otro proceso cuyo identificador de proceso se conoce.

 La diferencia entre las familias de **_exec** y **_spawn** es que una función **_spawn** puede devolver el control del nuevo proceso al proceso de llamada. En una función **_spawn**, tanto el proceso de llamada como el nuevo proceso están presentes en la memoria, a menos que se especifique **_P_OVERLAY**. En una función **_exec**, el nuevo proceso se superpone al proceso de llamada, por lo que el control no puede volver al proceso de llamada a menos que se produzca un error en el intento de iniciar la ejecución del nuevo proceso.

 Las diferencias entre las funciones de la familia de **_exec**, así como entre las de la familia de **_spawn**, guardan relación con el método usado para buscar el archivo que se ejecutará como el nuevo proceso, la forma en que los argumentos se pasan al nuevo proceso y el método de establecer el entorno, tal y como se muestra en la tabla siguiente. Utilice una función que pase una lista de argumentos cuando el número de argumentos sea constante o se conozca en tiempo de compilación. Utilice una función que pase un puntero a una matriz que contiene los argumentos cuando el número de argumentos deba determinarse en tiempo de ejecución. La información de la tabla siguiente también se aplica a sus homólogos de caracteres anchos de las funciones **_spawn** y **_exec**.

### <a name="spawn-and-exec-function-families"></a>Familias de _spawn y _exec (Función)

|Funciones|Utilizar la variable PATH para ubicar el archivo|Convención para pasar argumentos|Configuración del entorno|
|---------------|--------------------------------------|----------------------------------|--------------------------|
|**_execl**, **_spawnl**|No|Lista|Heredado del proceso de llamada|
|**_execle**, **_spawnle**|No|Lista|Puntero a la tabla de entorno para el nuevo proceso que se pasa como último argumento|
|**_execlp**, **_spawnlp**|Sí|Lista|Heredado del proceso de llamada|
|**_execvpe**, **_spawnvpe**|Sí|Matriz|Puntero a la tabla de entorno para el nuevo proceso que se pasa como último argumento|
|**_execlpe**, **_spawnlpe**|Sí|Lista|Puntero a la tabla de entorno para el nuevo proceso que se pasa como último argumento|
|**_execv**, **_spawnv**|No|Matriz|Heredado del proceso de llamada|
|**_execve**, **_spawnve**|No|Matriz|Puntero a la tabla de entorno para el nuevo proceso que se pasa como último argumento|
|**_execvp**, **_spawnvp**|Sí|Matriz|Heredado del proceso de llamada|

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
