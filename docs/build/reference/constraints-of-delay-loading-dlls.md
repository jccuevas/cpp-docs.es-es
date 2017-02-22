---
title: "Restricciones de las DLL de carga retrasada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "restricciones [C++], carga retrasada de archivos DLL"
  - "carga retrasada de archivos DLL, restricciones"
  - "DLL [C++], restricciones"
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Restricciones de las DLL de carga retrasada
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hay ciertas restricciones relacionadas con la carga retrasada de importaciones.  
  
-   No se pueden admitir las importaciones de datos.  Una solución alternativa consiste en administrar uno mismo la importación de datos de forma explícita con `LoadLibrary` \(o `GetModuleHandle` después de saber que la aplicación auxiliar de carga retrasada cargó la DLL\) y `GetProcAddress`.  
  
-   No se admite la carga retrasada de Kernel32.dll.  Esta DLL es necesaria para que las rutinas de la aplicación auxiliar de carga retrasada lleven a cabo la carga retrasada.  
  
-   No se admite el [enlace](../../build/reference/binding-imports.md) de puntos de entrada reenviados.  
  
-   Es posible que la carga retrasada de una DLL no tenga como resultado el mismo comportamiento del proceso si hay inicializaciones por procesos que se producen en el punto de entrada de la DLL de carga retrasada.  Entre otros casos, está el TLS \(almacenamiento local de subprocesos\) estático, que se declara con [\_\_declspec\(subproceso\)](../../cpp/thread.md) y no se administra al cargar la DLL con `LoadLibrary`.  El TLS dinámico, con `TlsAlloc`, `TlsFree`, `TlsGetValue` y `TlsSetValue`, sigue disponible para su uso en DLL estáticas o de carga retrasada.  
  
-   Los punteros de función estáticos \(globales\) se deben reinicializar a las funciones importadas después de la primera llamada a la función,  porque el primer uso del puntero de función apuntará al código thunk.  
  
-   Actualmente, con el mecanismo de importación normal, no hay ninguna manera de retrasar la carga de procedimientos específicos de una DLL solamente.  
  
-   No se admiten las convenciones de llamada personalizadas \(como, por ejemplo, el uso de códigos de condición en las arquitecturas x86\).  Además, los registros de punto flotante no se guardan en ninguna plataforma.  Si la rutina de la aplicación auxiliar personalizada o las rutinas de enlace utilizan tipos de punto flotante, tendrán que guardar y restaurar por completo el estado de punto flotante en las máquinas con convenciones de llamada de registro con parámetros de punto flotante.  Tenga cuidado al realizar la carga retrasada de la DLL de CRT si llama a funciones de CRT que tomen parámetros de punto flotante en una pila de procesador de datos numéricos \(NDP\) en la función de ayuda.  
  
## Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)   
 [Función LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175.aspx)   
 [Función GetModuleHandle](http://msdn.microsoft.com/library/windows/desktop/ms683199.aspx)   
 [Función GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)   
 [Función TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801.aspx)   
 [Función TlsFree](http://msdn.microsoft.com/library/windows/desktop/ms686804.aspx)   
 [Función TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812.aspx)   
 [Función TlsSetValue](http://msdn.microsoft.com/library/windows/desktop/ms686818.aspx)