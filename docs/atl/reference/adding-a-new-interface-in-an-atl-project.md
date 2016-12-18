---
title: "Agregar una nueva interfaz a un proyecto ATL | Microsoft Docs"
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
  - "vc.appwiz.ATL.interface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL projects, agregar interfaces"
  - "controles [ATL], interfaces"
  - "asistente para implementar interfaces de ATL"
  - "interfaces, agregar a objetos ATL"
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar una nueva interfaz a un proyecto ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando agregue una interfaz al objeto o control, puede crear funciones auxiliares para cada método de la interfaz.  En el objeto o control, puede agregar únicamente las interfaces que se encuentren actualmente en una biblioteca de tipos existentes.  Además, la clase a la que se agregue la interfaz deberá implementar la macro [BEGIN\_COM\_MAP](../Topic/BEGIN_COM_MAP.md) o, si el proyecto admite atributos, deberá tener el atributo `coclass`.  
  
 Puede agregar una nueva interfaz al control de dos maneras diferentes: manualmente o mediante asistentes para códigos en la Vista de clases.  
  
### Para utilizar asistentes para código en la Vista de clases con el fin de agregar una interfaz a un objeto o control existente  
  
1.  En la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario del mouse en el nombre de un control.  Por ejemplo, un control completo o un control compuesto, o cualquier otra clase de control que implemente una macro BEGIN\_COM\_MAP en su archivo de encabezado.  
  
2.  En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Implementar interfaz**.  
  
3.  Seleccione las interfaces para la implementación en el [Asistente para implementar interfaces](../../ide/implement-interface-wizard.md).  Si la interfaz no existe en una biblioteca de tipos disponible, deberá agregarla manualmente al archivo .idl.  
  
### Para agregar una nueva interfaz manualmente  
  
1.  Agregue la definición de la nueva interfaz al archivo .idl.  
  
2.  Derive el objeto o control desde la interfaz.  
  
3.  Cree una nueva macro [COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20\(ATL\).md) para la interfaz o, si el proyecto admite atributos, agregue el atributo `coclass`.  
  
4.  Implemente métodos en la interfaz.  
  
## Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C\+\+](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programar con ATL y código en tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [Configuraciones predeterminadas de un proyecto ATL](../../atl/reference/default-atl-project-configurations.md)