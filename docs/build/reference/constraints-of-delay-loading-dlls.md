---
title: Restricciones de DLL de carga retrasada | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd3f641a3ac03705ff7f3765d995d5c40bccda7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="constraints-of-delay-loading-dlls"></a>Restricciones de las DLL de carga retrasada
Hay ciertas restricciones relacionadas con la carga retrasada de importaciones.  
  
-   No se pueden admitir las importaciones de datos. Una solución alternativa consiste en administrar uno mismo la importación de datos de forma explícita con `LoadLibrary` (o `GetModuleHandle` después de saber que la aplicación auxiliar de carga retrasada cargó la DLL) y `GetProcAddress`.  
  
-   No se admite la carga retrasada de Kernel32.dll. Esta DLL es necesaria para que las rutinas de la aplicación auxiliar de carga retrasada lleven a cabo la carga retrasada.  
  
-   [Enlace](../../build/reference/binding-imports.md) de entrada no se admite puntos que se reenvían.  
  
-   Es posible que la carga retrasada de una DLL no tenga como resultado el mismo comportamiento del proceso si hay inicializaciones por procesos que se producen en el punto de entrada de la DLL de carga retrasada. Entre otros casos estático TLS (almacenamiento local de subprocesos), declarado mediante [__declspec (Thread)](../../cpp/thread.md), que no se controla al carga el archivo DLL con `LoadLibrary`. El TLS dinámico, con `TlsAlloc`, `TlsFree`, `TlsGetValue` y `TlsSetValue`, sigue disponible para su uso en DLL estáticas o de carga retrasada.  
  
-   Los punteros de función estáticos (globales) se deben reinicializar a las funciones importadas después de la primera llamada a la función, porque el primer uso del puntero de función apuntará al código thunk.  
  
-   Actualmente, con el mecanismo de importación normal, no hay ninguna manera de retrasar la carga de procedimientos específicos de una DLL solamente.  
  
-   No se admiten las convenciones de llamada personalizadas (como, por ejemplo, el uso de códigos de condición en las arquitecturas x86). Además, los registros de punto flotante no se guardan en ninguna plataforma. Si la rutina de la aplicación auxiliar personalizada o las rutinas de enlace utilizan tipos de punto flotante, tendrán que guardar y restaurar por completo el estado de punto flotante en las máquinas con convenciones de llamada de registro con parámetros de punto flotante. Tenga cuidado al realizar la carga retrasada de la DLL de CRT si llama a funciones de CRT que tomen parámetros de punto flotante en una pila de procesador de datos numéricos (NDP) en la función de ayuda.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga de retraso](../../build/reference/linker-support-for-delay-loaded-dlls.md)   
 [LoadLibrary (función)](http://msdn.microsoft.com/library/windows/desktop/ms684175.aspx)   
 [Función GetModuleHandle](http://msdn.microsoft.com/library/windows/desktop/ms683199.aspx)   
 [GetProcAddress (función)](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)   
 [TlsAlloc (función)](http://msdn.microsoft.com/library/windows/desktop/ms686801.aspx)   
 [TlsFree (función)](http://msdn.microsoft.com/library/windows/desktop/ms686804.aspx)   
 [TlsGetValue (función)](http://msdn.microsoft.com/library/windows/desktop/ms686812.aspx)   
 [TlsSetValue (función)](http://msdn.microsoft.com/library/windows/desktop/ms686818.aspx)