---
title: "Testing the Modified ATL DHTML Control | Microsoft Docs"
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
  - "DHTML controls, pruebas"
  - "controles HTML, pruebas"
  - "testing controls"
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Testing the Modified ATL DHTML Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Pruebe el nuevo control para ver cómo ahora funciona.  
  
#### Para compilar y probar el control modificado  
  
1.  Recompile el proyecto y ábralo en contenedor de prueba.  Vea [Propiedades y eventos de pruebas con el contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo tener acceso al contenedor de prueba.  
  
     Cambie el tamaño del control para mostrar todos los botones que agregó.  
  
2.  Examine los dos botones que insertó modificando HTML.  Cada botón contiene la etiqueta que se identificaron en [Modificación de Control ATL DHTML](../atl/modifying-the-atl-dhtml-control.md): **Actualizar** y **HelloHTML**.  
  
3.  Pruebe los dos nuevos botones para ver cómo funcionan.  
  
 Ahora pruebe los métodos que no forman parte de la interfaz de usuario.  
  
1.  Resalte el control, así que se provoca el borde.  
  
2.  En el menú de **Control** , haga clic en **Invoke Methods**.  
  
 Los métodos de la lista denominada **Nombre del método** son métodos que el contenedor puede llamar a: `MethodInvoked`y`GoToURL`.  El resto de los métodos se controlan mediante la interfaz de usuario.  
  
1.  Seleccione un método para invocar y haga clic en `Invoke` para mostrar el cuadro de mensaje de método o para navegar a www.microsoft.com.  
  
2.  En el cuadro de diálogo de **Invoke Methods** , haga clic en **Cerrar**.  
  
 Para obtener más información sobre los distintos elementos y archivos que componen un control ATL DHTML, vea [Identificar los elementos de proyecto de control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
## Vea también  
 [Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)