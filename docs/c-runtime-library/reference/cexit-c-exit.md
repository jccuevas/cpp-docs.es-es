---
title: "_cexit, _c_exit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_c_exit"
  - "_cexit"
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
  - "_cexit"
  - "c_exit"
  - "_c_exit"
  - "cexit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_c_exit (función)"
  - "_cexit (función)"
  - "c_exit (función)"
  - "cexit (función)"
  - "operaciones de limpieza durante procesos"
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _cexit, _c_exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realizar operaciones de limpieza y vuelve sin finalizar el proceso.  
  
## Sintaxis  
  
```  
void _cexit( void );  
void _c_exit( void );  
```  
  
## Comentarios  
 Llamadas de función `_cexit` , en pasado\- en, primero \- out orden de \(LIFO\), funciones registradas por `atexit` y `_onexit`.  Después `_cexit` vacía todos los búferes de E\/S y cierre las secuencias todo abiertos antes de volver.  `_c_exit` es igual que `_exit` pero vuelve al proceso de llamada sin procesar `atexit` o `_onexit` o vaciar los búferes de la secuencia.  El comportamiento de `exit`,de`_exit`, de `_cexit`, y de `_c_exit` se muestra en la tabla siguiente.  
  
|Función|Comportamiento|  
|-------------|--------------------|  
|`exit`|Realiza procedimientos de finalización completos de la biblioteca de c, finaliza el proceso, y deja con código de estado proporcionado.|  
|`_exit`|Realiza procedimientos de finalización rápidos de la biblioteca de c, finaliza el proceso, y deja con código de estado proporcionado.|  
|`_cexit`|Realiza procedimientos de finalización completos de la biblioteca de c y vuelve al llamador, pero no termina procesos.|  
|`_c_exit`|Realiza procedimientos de finalización rápidos de la biblioteca de c y vuelve al llamador, pero no termina procesos.|  
  
 Cuando se llama a las funciones de `_cexit` o de `_c_exit` , destructores para ningún objeto temporal o automática que existen en el momento de la llamada no se llaman.  Un objeto automático es un objeto definido en una función donde el objeto no se declara como static.  Un objeto temporal es un objeto creado por el compilador.  Para destruir un objeto automático antes de llamar a `_cexit` o `_c_exit`, explícitamente llama al destructor del objeto, como sigue:  
  
```  
myObject.myClass::~myClass( );  
```  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_cexit`|\<process.h\>|  
|`_c_exit`|\<process.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 [System::Diagnostics::Process::CloseMainWindow](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec, \_wexec \(Funciones\)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit, \_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_spawn, \_wspawn \(Funciones\)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, \_wsystem](../../c-runtime-library/reference/system-wsystem.md)