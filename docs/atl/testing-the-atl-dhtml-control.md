---
title: "Testing the ATL DHTML Control | Microsoft Docs"
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
  - "DHTML controls"
  - "DHTML controls, pruebas"
  - "controles HTML, pruebas"
  - "testing controls"
ms.assetid: 0e4b4358-80ce-4505-8b06-ef4f30b1d1f0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Testing the ATL DHTML Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una vez creado el proyecto, puede compilar y probar el ejemplo.  Antes de hacerlo, vista y el explorador de soluciones de la clase de uso para examinar el proyecto.  Los elementos del proyecto se describen con más detalle en [Identificar los elementos de proyecto de control DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
#### Para compilar y probar el control ATL DHTML  
  
1.  Compile el proyecto.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
2.  Cuando finalice la compilación, abra el contenedor de prueba.  Vea [Propiedades y eventos de pruebas con el contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo tener acceso al contenedor de prueba.  
  
3.  En contenedor de prueba, en el menú de **Editar** , haga clic **Insert New Control**.  
  
4.  En el cuadro de diálogo de **Insertar control** , seleccione el control listbox.  Recuerde, su nombre se basa en el nombre corto indicada en el asistente para controles ATL.  Haga clic en **Aceptar**.  
  
5.  Examine el control.  Observe que tiene una barra de desplazamiento.  Utilice los identificadores de control para cambiar el tamaño del control para activar la barra de desplazamiento.  
  
6.  Pruebe los botones del control.  Cambia el color de fondo en el color indicado por el botón.  
  
7.  Contenedor de prueba próximo.  
  
 Siguiente, intente [modificar el control DHTML](../atl/modifying-the-atl-dhtml-control.md).  
  
## Vea también  
 [Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)