---
title: "Compatibilidad con COM+ 1.0 en proyectos ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.MTS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL projects, compatibilidad con COM+ 1.0"
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad con COM+ 1.0 en proyectos ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede utilizar el [Asistente para proyectos ATL](../../atl/reference/creating-an-atl-project.md) para crear un proyecto con compatibilidad básica para los componentes de COM\+ 1.0.  
  
 COM\+ 1.0 está diseñado para desarrollar aplicaciones distribuidas basadas en componentes.  También proporciona una infraestructura en tiempo de ejecución para implementar y administrar estas aplicaciones.  
  
 Si activa la casilla **Admitir COM\+ 1.0**, el asistente modifica el script de compilación en el paso de vinculación.  Específicamente, el proyecto COM\+ 1.0 se vincula a las siguientes bibliotecas:  
  
-   comsvcs.lib  
  
-   Mtxguid.lib  
  
 Si activa la casilla **Admitir COM\+ 1.0**, también puede seleccionar **Admitir registro de componentes**.  El registrador de componentes permite al objeto COM\+ 1.0 obtener una lista de componentes, registrar componentes o eliminar componentes del registro \(individualmente o todos a la vez\).  
  
## Vea también  
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Configuraciones predeterminadas de un proyecto ATL](../../atl/reference/default-atl-project-configurations.md)