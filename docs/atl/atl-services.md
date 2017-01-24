---
title: "Servicios ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "servicios ATL"
  - "objetos COM, ATL"
  - "CServiceModule (clase)"
  - "servicios, ATL"
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Servicios ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para crear el objeto ATL COM de manera que se ejecute en un servicio, seleccionar Service \(EXE\) de la lista de opciones de servidor en el asistente para proyectos ATL.  Después el asistente creará una clase derivada de `CAtlServiceModuleT` para implementar el servicio.  
  
 Cuando el objeto COM ATL se compila como un servicio, se registrará solo como servidor local, y no aparecerá en la lista de servicios en el Panel de control.  Esto es porque es más fácil depurar el servicio como servidor local de como un servicio.  Para instalarla como servicio, ejecute lo siguiente en el símbolo del sistema:  
  
 `YourEXE` `.exe /Service`  
  
 Para desinstalar, ejecute lo siguiente:  
  
 `YourEXE` `.exe /UnregServer`  
  
 Los primeros cuatro temas de esta sección explican las acciones que se producen durante la ejecución de las funciones miembro de `CAtlServiceModuleT` .  Estos temas aparecen en la misma secuencia que las funciones se denominan normalmente.  Para mejorar la comprensión de estos temas, es conveniente utilizar el código fuente generado por el asistente para proyectos ATL como referencia.  Estos cuatro primeros temas son:  
  
-   [El CAtlServiceModuleT:: Función inicial](../atl/catlservicemodulet-start-function.md)  
  
-   [El CAtlServiceModuleT:: función de ServiceMain](../atl/catlservicemodulet-servicemain-function.md)  
  
-   [El CAtlServiceModuleT:: Función de ejecución](../atl/catlservicemodulet-run-function.md)  
  
-   [El CAtlServiceModuleT:: Función controladora](../atl/catlservicemodulet-handler-function.md)  
  
 Los tres temas que tratan los conceptos relacionados con el desarrollo de un servicio:  
  
-   [Entradas del Registro](../atl/registry-entries.md) para servicios de ATL  
  
-   [DCOMCNFG](../atl/dcomcnfg.md)  
  
-   [Sugerencias de depuración](../atl/debugging-tips.md) para servicios de ATL  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)