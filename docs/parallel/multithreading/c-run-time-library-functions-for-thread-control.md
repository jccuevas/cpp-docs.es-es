---
title: "Funciones de la biblioteca en tiempo de ejecuci&#243;n de C para el control de subprocesos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_beginthread (función)"
  - "_beginthreadex (función)"
  - "_endthread (función)"
  - "_endthreadex (función)"
  - "subprocesamiento múltiple [C++], controlar subprocesos"
  - "subprocesamiento [C++], controlar subprocesos"
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones de la biblioteca en tiempo de ejecuci&#243;n de C para el control de subprocesos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Todos los programas Win32 contienen al menos un subproceso.  Cualquier subproceso puede crear subprocesos adicionales.  Un subproceso puede completar su trabajo rápidamente y después terminar, o bien puede permanecer activo durante toda la vida del programa.  
  
 Las bibliotecas en tiempo de ejecución LIBCMT y MSVCRT C proporcionan las siguientes funciones para la creación y terminación de subprocesos: [\_beginthread, \_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) y [\_endthread, \_endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md).  
  
 Las funciones `_beginthread` y `_beginthreadex` crean un nuevo subproceso y devuelven un identificador del subproceso si la operación se ha realizado correctamente.  El subproceso termina automáticamente una vez que completa su ejecución, o bien puede terminarse explícitamente mediante una llamada a `_endthread` o `_endthreadex`.  
  
> [!NOTE]
>  Si va a realizar llamadas a rutinas en tiempo de ejecución de C desde un programa compilado con Libcmt.lib, deberá iniciar cada subproceso con la función `_beginthread` o `_beginthreadex`.  No utilice las funciones `ExitThread` y `CreateThread` de Win32.  La utilización de `SuspendThread` puede producir un interbloqueo cuando existe más de un subproceso bloqueado en espera de que el subproceso suspendido complete su acceso a una estructura de datos en tiempo de ejecución de C.  
  
##  <a name="_core_the__beginthread_function"></a> Funciones \_beginthread y \_beginthreadex  
 Las funciones `_beginthread` y `_beginthreadex` crean un nuevo subproceso.  Un subproceso comparte los segmentos de código y de datos de un proceso con otros subprocesos del proceso pero dispone de sus propios y únicos valores de registros, espacio de pila y dirección de la instrucción actual.  El sistema asigna tiempo de CPU a cada subproceso, de modo que todos los subprocesos de un proceso puedan ejecutarse de forma simultánea.  
  
 Las funciones `_beginthread` y `_beginthreadex` son similares a la función [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) de la API Win32, pero presentan estas diferencias:  
  
-   Inicializan ciertas variables de la biblioteca en tiempo de ejecución de C.  Esto sólo es importante cuando se utiliza la biblioteca en tiempo de ejecución de C en los subprocesos.  
  
-   `CreateThread` ayuda a proporcionar control sobre los atributos de seguridad.  Esta función se puede utilizar para iniciar un subproceso que se encontraba en un estado suspendido.  
  
 `_beginthread` y `_beginthreadex` devuelven un identificador al nuevo subproceso si se han realizado correctamente o un código de error si se produjo un error.  
  
##  <a name="_core_the__endthread_function"></a> Funciones \_endthread y \_endthreadex  
 La función [\_endthread](../../c-runtime-library/reference/endthread-endthreadex.md) termina un subproceso creado por `_beginthread` \(y de igual forma, `_endthreadex` termina un subproceso creado por `_beginthreadex`\).  Los subprocesos terminan automáticamente cuando finalizan.  `_endthread` y `_endthreadex` son útiles para la terminación condicional desde un subproceso.  Por ejemplo, un subproceso dedicado a procesar las comunicaciones puede terminar si es incapaz de obtener el control del puerto de comunicaciones.  
  
## Vea también  
 [Subprocesamiento múltiple con C y Win32](../../parallel/multithreading-with-c-and-win32.md)